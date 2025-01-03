<div>

<div>

<div>

<div>

### 1.5.18. How can I write custom crawler using PL?

</div>

</div>

</div>

The following code is an example of loading data via crawler with
special function to generate link for downloading:

``` programlisting
create procedure EUROPEANA_STORE (
  in _host varchar,
  in _url varchar,
  in _root varchar,
  inout _content varchar,
  in _s_etag varchar,
  in _c_type varchar,
  in store_flag int := 1,
  in udata any := null,
  in lev int := 0)
{
   declare url varchar;
   declare xt, xp any;
   declare old_mode int;
   xt := xtree_doc (_content, 2);
   xp := xpath_eval ('//table//tr/td/a[@href]/text()', xt, 0);
   commit work;
   old_mode := log_enable (3,1);
   foreach (any u in xp) do
     {
       u := cast (u as varchar);
       url := sprintf ('http://semanticweb.cs.vu.nl/europeana/api/export_graph?graph=%U&mimetype=default&format=turtle', u);
       dbg_printf ('%s', u);
     {
       declare continue handler for sqlstate '*' {
         dbg_printf ('ERROR: %s', __SQL_MESSAGE);
       };
       SPARQL LOAD ?:url into GRAPH ?:u;
     }
     }
   log_enable (old_mode, 1);
   return WS.WS.LOCAL_STORE (_host, _url, _root, _content, _s_etag, _c_type, store_flag, 0);
}
```

<div>

|                            |                                                                     |
|:--------------------------:|:--------------------------------------------------------------------|
| ![\[Tip\]](images/tip.png) | See Also:                                                           |
|                            | <a href="admui.webservices.html#contentcrawlerrdf" class="link"     
                              title="Set Up the Content Crawler to Gather RDF">Set Up the Content  
                              Crawler to Gather RDF</a>                                            |

</div>

</div>
