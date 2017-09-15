# filebrowser

A filebrowser that connects to a backend API to display some filesystem.
It caches pretty hard.

Make sure to include `filebrowser.css` and one of the js files from the `dist` directory.
Call the `filebrowser.init` function when you are ready to display the filebrowser.
Parameters:
   - `containerId` -- *Required* The css id for the container that the filebrowser will be put in.
   - `fetchFunction` -- *Required* The function to call to get directory listings.
   - `directLinkFunction` -- *Optional* A function to get a link to the contents for a file.
   - `options` -- *Optional* Additional options.
   - ` `callback` -- *Optional* Called with no parameters when the filebrowser is fully loaded (including the cache).

A fetch function has the following parameters:
   - `direntId` -- *Required* The identifier for the dirent being fetched. Empty string for root.
   - `callbak` -- *Required* Called once the backend fetch completes. Has the following parameters:
      - `direntsFetched` -- *Required* A list of `filebrowser.DirEnt` that were fetched.
      - `parentIdOfDirents` -- *Required* The parent of the dirents fetched. There can only be one parent. Root can be its own parent.

Direct link functions are used to compute a link from a filebrowser.File.
This can be useful in cases like when you need to atatch an authentication token to a request.
These functions take a filebrowser.File and return a link that can be used to get the contents of the file.
