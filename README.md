# Prismic + Nuxt Web App

Web app built for the Kentville Marlins Swim Team and carefully crafter by **evanmarshall.dev**: [Check Out the Portfolio][evan-dev].

## Resources Used

- **Prismic**: [Check Out Prismic][prismic]
- **Nuxt**: [Check Out Nuxt][nuxt]
- **YouTube Tutorial**: [Check Out the Tutorial for this Project][youtube-tut]

&nbsp;

## 🚀 Quick Start

To start a new project using this starter, run the following commands in your terminal:

```sh
pnpx @slicemachine/init@latest --repository >your-project-name< --starter nuxt-starter-prismic-minimal
cd your-project-name
pnpx @slicemachine/init@latest
```

When you're ready to start your project, run the following command:

```sh
pnpm run dev
```

## How to use your project

To edit the content of this project, go to [prismic.io/dashboard](https://prismic.io/dashboard), click on the repository for this website, and start editing.

### Create a page

To create a page, click on the green pencil icon, then select **Page**.

Pages are made of Slices. You can add and rearrange Slices to your pages.

Your new page will be accessible by its URL, but it won't appear on the website automatically. To let users discover it, add it to the navigation.

### Preview documents

If you launched this starter when you created a new repository in the Prismic Dashboard, then your repository is preconfigured with previews in development on localhost:3000.

To add a production preview, option your repository and go to _Settings > Previews_. Under _Create a New Preview_, fill in the three fields:

- a name (like **Production**)
- the domain where your app is running (like <https://www.yoursite.com>)
- `/api/preview` for the Preview Route

Now, go to a draft document and click the eye icon in the top-right corner.

To learn more about how to configure previews, read [Preview Drafts in Nuxt](https://prismic.io/docs/technologies/nuxt-preview-drafts) in the Prismic documentation.

### Customize this website

This website is preconfigured with Prismic. Functionality is provided by the `@nuxtjs/prismic` package, which makes Prismic utilities available throughout the app. Take a look at the code to see how it's used.

### Edit the code

There are two steps to rendering content from Prismic in your Nuxt project:

1. Fetch content from the Prismic API
2. Template the content

Here are some of the files in your project that you can edit:

- `nuxt.config.js` - The `prismic` property includes configurations for `@nuxtjs/prismic`.
- `pages/index.vue` - This is the app homepage. It queries and renders a page document with the UID (unique identifier) "home" from the Prismic API.
- `pages/[uid].vue` - This is the page component, which queries and renders a page document from your Prismic repository based on the UID.
- `slices/RichText/index.vue` - Each Slice has an `index.vue` file that renders the Slice component. Edit this file to customize your Slices.

These are important files that you should leave as-is:

- `pages/slice-simulator.vue` - Do not edit or delete this file. This file simulates your Slice components in development.
- `slices/` - This directory contains Slice components, which are generated programmatically by Slice Machine. To customize a Slice template, you can edit the Slice's `index.vue` file. To add Slices, delete Slices, or edit Slice models, use Slice Machine (more info below).

### Deploy to the web

To put your project online, see [Deploy your Nuxt App](https://prismic.io/docs/technologies/nuxt-deploy).

### Edit content models with Slice Machine

This project includes an application called Slice Machine, which generates models for your Custom Types and Slices. Slice Machine stores the models locally in your codebase, so you can save and version them. It also syncs your models to Prismic. To learn how to use Slice Machine, read [Model Content in Nuxt](https://prismic.io/docs/technologies/nuxt-model-content).

If you change or add to your Custom Types, you'll need to update your route handling to match. To learn how to do that, read [Define Paths in Nuxt](https://prismic.io/docs/technologies/nuxt-define-routes).

## Notes

### Getting Started

In `nuxt.config.ts` you will see that `compatibilityVersion: 4` is being used as a **_feature_** flag, which means we are using Nuxt v4 features before version 4 is released. We are using Nuxt v3.

The `app` directory contains all code used to build the frontend of the app whereas the `server` directory contains serverside things **_api routes_**, **_middlewares_**, etc.

### Configure Tailwind CSS in Nuxt

With **_Nuxt Modules_** you can easily enable **_TailwindCSS_** within our app using `pnpx nuxi module add tailwindcss` and this will add tailwind to the `nuxt.config.ts` as a **_module_**. Next we will create a tailwind.config.ts file and enter in some configs found below:

```config
import type { Config } from 'tailwindcss'

export default <Partial<Config>>{
  content: ["./app/**/*.{js,ts,vue}"]
}
```

> [!NOTE]
>
> [Tailwind for Nuxt Apps][nuxt-tailwind]

### Installing Nuxt Fonts

To add Nuxt Fonts to the project run `pnpx nuxi module add fonts`. This will add fonts to the `nuxt.config.ts` as a **_module_**.

Next we go to the `app` dir and create a file under `assets/css/main.css`. Within this file you simply add the font family to the body:

```css
body {
  font-family: "DM Sans", sans-serif;
}
```

This tells Nuxt that we want to use the **_DM Sans_** font and it installs it for us as well.

Next we need to add **_css_** to the `nuxt.config.ts`:

```config
css: ["~/assets/css/main.css"]
```

Make sure to comment out the default font set in `app/slices/RichText/index.vue`.

> [!NOTE]
>
> [Nuxt Fonts][nuxt-fonts]

[prismic]: https://prismic.io
[nuxt]: https://nuxt.com
[evan-dev]: https://www.evanmarshall.dev
[youtube-tut]: https://www.youtube.com/watch?v=EmvCh7Jb0Mw&t=307s
[nuxt-tailwind]: https://tailwindcss.nuxtjs.org/
[nuxt-fonts]: https://fonts.nuxt.com/
