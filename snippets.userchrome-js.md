
## snippets
```js
function setClipboard(dat) {
  let str = Cc["@mozilla.org/supports-string;1"].createInstance(
    Ci.nsISupportsString
  );
  str.data = dat;
  let transferable = Cc["@mozilla.org/widget/transferable;1"].createInstance(Ci.nsITransferable);
  transferable.init(getLoadContext());
  transferable.addDataFlavor("text/plain");
  transferable.setTransferData("text/plain", str);
  Services.clipboard.setData(
    transferable,
    null,
    Ci.nsIClipboard.kGlobalClipboard
  );
}
```

```js
gBrowser.adoptTab
a = UC_API.Windows.getAll()
b = a[1].gBrowser.adoptTab(t)

window.docShell.messageManager // mm


// how to store global state?
// with class based objects per-window?
globalThis.a = new a()


// open in new tab
const { BrowserWindowTracker } = await import('resource:///modules/BrowserWindowTracker.sys.mjs')
BrowserWindowTracker.openWindow()

// get profile path
let ProfilePathChrome = PathUtils.toFileURI(PathUtils.join(PathUtils.profileDir, 'chrome'));

// open trusted url in new tab
URILoadingHelper.openTrustedLinkIn(window, 'about:preferences', 'tab');

// duplicate current tab
const nt = gBrowser.duplicateTab(gBrowser.selectedTab);
gBrowser.selectedTab = nt;

// what's this?
gBrowser.selectedBrowser.getAttributeNames() // seems like attributes on the <tabbrowser> element.

// show notification
UC_API.Notifications.show({
    label : "Welcome to ium! To get the full Geckium experience, download Geckium from Releases or compile your chrome folder.",
    type : "geckium-notification",
    priority: "critical"
});


// get tabs in MRU (most recently used) order.
SessionStore.getCurrentState().windows
    .flatMap(win => win.tabs)
    .sort((a, b) => b.lastAccessed - a.lastAccessed);



// can we navigate to a tab while not updating the
// 'lastAccessed' time?
// If not, calling 'navigate -1 by lastAccessed time will just switch between two tabs
//
// if so, we can implement functionality like a jumplist
// for buffers in neovim
```
