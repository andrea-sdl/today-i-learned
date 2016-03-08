# Moxie FileInput has issues with hidden fields #

The Moxie fileInput (useful for file upload) redraws a field _over_ your button.
It works beautifully but if your button (or your trigger point) is hidden then you're better using the refresh on the FileInput object to make sure it's drawn correctly.

[http://output.jsbin.com/bokiqopoga](Example of the bug)