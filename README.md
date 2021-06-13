# Lawline Checkpoint Verifier
This simple browser console script automatically acknowledges and dismisses the [Lawline](https://www.lawline.com) checkpoint verification modal without requiring user interaction, allowing the user uninterrupted access to their precious continuing legal education (CLE) videos.

## Usage
1. Visit any video course on the Lawline website and begin playing the video.
2. Open the browser console window (press `Ctrl + Shift + K` in Firefox).
3. Paste the following code into the console and press `Enter`:
```javascript
var observer = new MutationObserver(function(mutations) {
    mutations.forEach(function(mutation) {
        if(mutation.target.style.display != 'none') {
            if(modalButton = document.body.querySelector('.verification-checkpoint-modal button.btn')) {
                setTimeout(() => {
                    modalButton.click();
                    console.log('SUCCESS: Verfication checkpoint passed!');
                }, 3000);
            } else {
                console.log('ERROR: Verification checkpoint failed!');
            }
        }
    });    
});

var target = document.getElementsByClassName('verification-checkpoint-modal')[0];
observer.observe(target, { attributes : true, attributeFilter : ['style'] });
```
4. That's it! The script will report any success or failure to dismiss the modal in the console, so leave the console window open for easier monitoring.

## Disclaimer
This script was made for educational purposes only and is not intended to assist the end user in circumventing the continuing education process. Regardless of whether or how any user uses this script, attorneys are required to receive and accurately report continuing education credits and are, of course, bound by ethical obligations regarding dishonesty. Use this script accordingly.
