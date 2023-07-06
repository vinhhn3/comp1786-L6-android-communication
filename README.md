# Intercept User Actions

We will use a WebViewClient to intercept the user clicking on a link

To achieve this, we will add an inner class in `MainActivity.java`

```java
package com.example.comp1786_l6_android_communication;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.webkit.WebResourceRequest;
import android.webkit.WebView;
import android.webkit.WebViewClient;

public class MainActivity extends AppCompatActivity {

    private WebView browser;

    private final String url = "https://www.google.com/";

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        browser = findViewById(R.id.myWebView);

        browser.getSettings().setBuiltInZoomControls(true);

        // The inner class handles events that it chooses to override
        browser.setWebViewClient(new BrowserDemoWebViewClient());

        browser.loadUrl(url);
    }
    // Add inner class
    // Inherits from WebViewClient
    private class BrowserDemoWebViewClient extends WebViewClient {
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, WebResourceRequest request){
            // We just load the URL into the view rather than launching the external browser
            view.loadUrl(request.getUrl().toString());
            return true;
        }
    }
}
```

Voila, now when we click on the link, we will not launch the Browser and continue to use WebView

![img_1.png](img_1.png)

![img_2.png](img_2.png)
