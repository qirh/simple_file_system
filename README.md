## Simple File System

App is deployed to Vercel: https://simple-file-system.vercel.app/

### Notes
- This is a simple SPA built using React and Typescript.
- The UI is styled using [98.css](https://jdan.github.io/98.css/).
- I chose to use external storage (Vercel Blob) instead of bundling assets directly into the SPA.
    - The easiest solution to build was to package the assets within the SPA, however this would inflate the app size significantly since this is a simple SPA with no backend/server. It would also mean that the initial app load would be slower and all the assets would be loaded regardless of whether or not they are actually used.
    - What I opted to build is just one step more complicated than the easiest solution. Instead of packaging all the assets with the app. I uploaded them to Vercel Blob storage, and they are simply fetched from storage when they are needed, keeping the app size manageable and ensuring a faster app initial load time.
    - The reason the assets are not loaded from `sec.gov` is because of a restrictive header `X-Frame-Options: SAMEORIGIN`, which prevents embedding content from their website in iframes.

### This is a very simple project, many things are not implemented. For example:
- No search or sort functionality for files/folders.
- No Create/Edit/Delete files or folders. Just able to view.
- No tests.
- No mobile support.
- No error handling, if a network call fails, the app will stop working, there are no re-tries or fallbacks.
- The blob store:
    - It is kept open to the public, and all its contents are also public. This is done for the ease of development. However, that comes with a security risk. Also, the json was modified with the new `sourceLink` for the HTML files in blob storage.
    - There is no caching.
- Simple routing system based on the `state` of the parent component. As a result, no URL path navigation (refreshing the page resets the view).
    - If this project was anything more complex, I would use `react-router` or a similar solution for routing.