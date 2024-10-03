# Install packages
================================

**Author**: Lien Chen  **Date**: 2020-09-04

* Use javascript and jquery to load ajax with php file
* after success the ajax and run the success method

```php
<button onclick="test()">test</button>
<script>
function test() {
    $.ajax({
        type: "POST",
        url: "Test.php",
        data: infoPO,
        success: function() {   
            window.location.reload();  
        }
    });
}
</script>
```