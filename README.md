# Intercept Back Button

Modify function `shouldOverrideUrlLoading()` to not allow to leave `google.com`

```java
    private class BrowserDemoWebViewClient extends WebViewClient{
    @Override
    public boolean shouldOverrideUrlLoading(WebView view, WebResourceRequest request){
        try{
            URL targetURL = new URL(request.getUrl().toString());
            String hostURL = targetURL.getProtocol() + "://" + targetURL.getHost();
            if(hostURL.equalsIgnoreCase(url)){
                view.loadUrl(targetURL.toString());
            }
            else{
                Toast.makeText(getApplicationContext(),
                        "Sorry you can't leave google.com",
                        Toast.LENGTH_LONG
                ).show();
            }
        }
        catch(MalformedURLException e){
            e.printStackTrace();
        }
        return true;
    }
}
```

Now, we can't leave `google.com`

```java
    private class BrowserDemoWebViewClient extends WebViewClient{
        @Override
        public boolean shouldOverrideUrlLoading(WebView view, WebResourceRequest request){
            try{
                URL targetURL = new URL(request.getUrl().toString());
                String hostURL = targetURL.getProtocol() + "://" + targetURL.getHost();
                if(hostURL.equalsIgnoreCase(url)){
                    view.loadUrl(targetURL.toString());
                }
                else{
                    Toast.makeText(getApplicationContext(),
                            "Sorry you can't leave google.com",
                            Toast.LENGTH_LONG
                    ).show();
                }
            }
            catch(MalformedURLException e){
                e.printStackTrace();
            }
            return true;
        }
    }
```
