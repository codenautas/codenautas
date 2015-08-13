# code injection

## code injection in jQuery

How to avoid it?

**Never, build HTML code by adding strings that contents data**

insted of                                          | write
---------------------------------------------------|-------------------------------------------------
`$('#id').html('<p>'+value+'</p>')`                | `$('#id').append($('<p>').text(value))`
`$('#id').html('<img src="'+url+'">')`             | `$('#id').append($('<img>').attr('src',url))`
