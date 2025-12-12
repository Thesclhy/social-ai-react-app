# Social AI

React web app that blends AI image generation with a social-style gallery. Users can describe scenes to create images with OpenAI, upload them, browse/delete their own media, and search collections by user or keyword.

## Features
- AI landing page: prompt DALL·E for images, preview in a lightbox, and upload the generated result.
- Auth: login/register flows backed by the configured API.
- Collections: tabbed photo/video gallery with delete controls, search (all/keyword/user), and responsive navbar.
- Create post: modal form to upload images or videos.

## Tech stack
React (CRA), React Router, MUI + Ant Design UI, OpenAI SDK, react-photo-album, yet-another-react-lightbox, axios, styled-components, http-proxy-middleware.

## Getting started
1) Install dependencies
```
npm install
```

2) Add environment variables (not committed; `.env` is gitignored)
```
REACT_APP_OPENAI_KEY=your_openai_api_key
```

3) Run locally
```
npm start
```
The app runs at http://localhost:3000.

4) Build for production
```
npm run build
```

## Configuration
- API backend: `src/constants.js` sets `BASE_URL` for auth/posts/search. Adjust if you host your own backend.
- OpenAI: the key is read from `REACT_APP_OPENAI_KEY`. For production, set it via your hosting provider’s environment settings (GitHub Secrets, AWS Amplify/EB/EC2, etc.) rather than committing a `.env`.
- Media proxy: `src/setupProxy.js` proxies `/api` to the blob storage host used when downloading generated images, to avoid CORS issues. Leave it in place unless you change where images are fetched from.

## Scripts
- `npm start` — dev server
- `npm test` — CRA test runner
- `npm run build` — production build

## Security notes
- Do not expose real API keys in public frontends. This demo calls OpenAI from the client; for production, front key usage through a backend or function proxy and store secrets in your platform’s secret manager.
- `.env` stays local and is ignored by git; set env vars separately in CI/hosting.

## License
MIT (see LICENSE). Replace with your preferred license if needed.
