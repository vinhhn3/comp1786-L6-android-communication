# Intercept Back Button

Now the new page is loaded into the WebView

However, the effect of the user clicking the phone's back button is probably not what they want

It takes them out of the app, probably back to the home screen

We can fix that by intercepting the phone's back button and making it act like a browser's back button

Add the following code `MainActivity.java`

```java
    @Override
    public boolean onKeyDown(int keyCode, KeyEvent event){
        // Check if the user clicked the Back button
        if((keyCode == KeyEvent.KEYCODE_BACK)
                // Check if there is any history in the browser to go back to
                && browser.canGoBack()
        ){
            browser.goBack();
            return true;
        }

        // If another key was pressed, then let the super class handle it
        return super.onKeyDown(keyCode, event);
    }
```
