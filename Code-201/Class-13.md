# Class 13 - Local Storage

## Local Storage and How To Use It On Websites

1. Why would a developer use local storage for a web application?
   * When you use an application and then close it, its state will be reset the next time you open it. We need to store the state of your interface on the local storage. <https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/>
2. What information should not be stored in local storage?
   * Unsecure information, local storage is not secure.
3. Local storage can store what type of data? How would you convert it to that type before storing?
   * You can only store strings in the different keys. You can work around this by using the native JSON.stringify() and JSON.parse() methods. <https://www.smashingmagazine.com/2010/10/local-storage-and-how-to-use-it/>
