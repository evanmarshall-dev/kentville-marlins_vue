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

### Slicemachine

Enter **_slicemachine_** by typing `pnpm slicemachine`. This opens the slicemachine development environment where we can create and change data models while benefitting from versioning, previews, and auto-generated marks for us.

We can create three types of **_data models_**:

1. **Page types**: For pages, blog posts, and landing pages for example. Anything that will have a URL.
2. **Custom Types**: More abstract content collections. For example, a taxonomy collection, navigation document, and settings document.
3. **Slices**

#### Custom Type

Let's create a **_settings document_**.

1. Click custom types in slicemachine and select create.
2. Select **reusable** type or **single** type.
3. Select single type since we will only have one instance of this document inside prismic.
4. Name the document.
5. Click create.

Now we are brought to a page for settings document. There is a **main** tab and you can add, edit, and remove tabs. Tabs are a way to organize content for content writers.

Within the main tab we have two zones: **_static zone_** and **_slices_**.

Next, we will add some **_fields_** inside the static zone (i.e. text field or image). The fields will indicate to a content writer what to add as content.

After completing the Settings Document locally, you will see a custom type directory created with an `index.json` found within a settings directory (`/customtypes/settings/index.json`). The `index.json` will contain everything we just configured within slicemachine as a **_json object_** that prismic understands.

### Adding Content to Prismic Production

To add all of the above local changes to prismic, we go to **_Review Changes_** and click **_Push_**.

#### Page Builder

First go to **_Create a New Page_** and you will se we have access to our **_settings_** page we just created. This is where we input the content for the site.

After entering the content into the settings document, we will hit **save** and **publish**.

Now we need to create a folder called **_layouts_** within the local app (`/app/layouts`). Within this new directory we want to create a `default.vue`. This is the default layout we want to use on every page. Default is a special keyword that indicates it will be applied on all pages of the website.

To get this content to prismic we use the prismic SDK, which can be found in nuxt config file under modules (`@nuxtjs/prismic`).

Within the default.vue layout we first get the prismic object (`usePrismic()`). This object is injected into nuxt app using **_auto imports_**. This allows us to get access to the prismic client to gather content.

Next we add data constant as settings key and use **_async_** data method to query our content. useAsyncData allows us to query on the server or the client based on the context the app is rendered on and we use this data to render our website. There are a lot of methods to get data from the prismic client (i.e. getAllByType, or getByID).

We want to get our settings document which is a single type so we use the `getSingle` method.

Now within the template we can print the settings (`{{settings}}`). Now if we go back to the local app we see settings JSON data printed, which we will use to render our header and our footer.

For now we will use it just to define our meta data. This is done by using `useSeoMeta()`.

```vue
<script lang="ts" setup>
const prismic = usePrismic();

const { data: settings } = await useAsyncData(() =>
  prismic.client.getSingle("settings")
);

useSeoMeta({
  title: settings.value?.data.site_title,
  ogTitle: settings.value?.data.site_title,
  description: settings.value?.data.meta_description,
  ogDescription: settings.value?.data.meta_description,
  ogImage: computed(() => prismic.asImageSrc(settings.value?.data.meta_image)),
});
</script>

<template>
  <div>
    {{ settings }}
    <slot />
  </div>
</template>
```

### Site Header and Footer

The header and footer are components so they are found in `/app/components/` directory. For the header just add the script section and template section. Within template just put placeholder header element for now.

We fetched settings from prismic in the `default.vue` and we need to make them available to `AppHeader.vue`. We do this by assigning a **_props_** to the header. We first define a prop with a typescript type. The props is defined within the `<>`. Assign `settings` object to `Content.Settings` (settings document) from prismic. The Content imported from **_prismicio client_** is where you will find all of your prismic types. The content type we want is `SettingsDocument`.

**To summarize**: We want a prop called settings and we want the content of the prop to be a settings document from prismic.

Now we can go back to `default.vue` and add the AppHeader component with a settings prop containing the settings document.

> [!NOTE]
> Make sure when creating the component that you add `?` symbol after settings because when using the `useAsyncData` in the `default.vue` it can also be undefined as well as settings document.

#### Build the Header

Remove `{{settings}}` from default.vue so the JSON does not display on browser.

Make sure the SVG folder for header goes in the `components` directory. Change the extension for logo to vue and wrap the contents within a `<template></template>`. Now we can add `<GlideLogo />` component to the header.

> [!NOTE]
> Make sure to add `aria-label="Main"` to the nav element in the header to indicate for accessibility that this is the main navigation.

Go back to slice machine (`pnpm slicemachine`), click **Custom Types** then **Settings** then **Show code snippets**. The code snippets will show how you can render links for the header (Make sure to add `settings?.` to `data.navigation`).

The **About**, **Schedules**, **Register Now** will show up in the navigation now as these were created in Settings on page builder (Change temoplate to a list item).

```vue
<li v-for="link in settings?.data.navigation" :key="link.key">
  <PrismicLink :field="link" :class="link.variant" />
</li>
```

Now we will create a link for the `GlideLogo`.

```vue
<NuxtLink to="/">
  <GlideLogo />
</NuxtLink>
```

Now to add mobile navigation menu. See below for code. We need to add logic for opening and closing the mobile menu (hamburger and cross icon).

Add `const isOpen = ref(false)` and wrap the NuxtLink and logo in a div with display flex. Add `@click="isOpen = false"` to the NuxtLink. Then add button with `@click="isOpen = true"`. Then we add logic to the div containing the mobile menu for adding a class if `isOpen` is available translate x to 0 width and if not then translate x to full width (`:class="isOpen ? 'translate-x-0' : 'translate-x-full'"`).

> [!NOTE]
> The `will-change-transform` tailwind class provides CSS hint that this class will change and the browser will optimize transition to be as smooth as possible.

Install nuxt icons to replace the open and close.

Now to style the `PrismicLink` for the nav items.

To style a different `link.variant` property (i.e. Link or Button), which were designed in slicemachine under `/Custom types/Settings/Navigation`, can be used to determine link or button. You can do this by making the button a dedicated component with a bunch of functionality, but in this case we will just create a class (`:class="{ buttonLink: link.variant === 'Button' }"`). Because we will use this button component in several parts of the website we will make the class (buttonLink) global in the `main.css`.

```vue
<!-- Mobile navigation. -->
<div
  class="md:hidden fixed inset-0 z-40 flex flex-col items-end bg-gray-950 pr-4 pt-6"
>
  <ul class="grid justify-items-end gap-6">
    <li v-for="link in settings?.data.navigation" :key="link.key">
      <PrismicLink :field="link" :class="link.variant" />
    </li>
  </ul>
</div>
```

```css
.buttonLink {
  /* Structure styles */
  @apply relative inline-flex h-fit w-fit rounded-full px-4 py-2;
  /* Color styles */
  @apply border border-sky-100/20 bg-sky-200/10 text-sky-200 outline-none ring-teal-300;
  /* After styles (Can also do with pseudo class after)  */
  @apply after:absolute after:inset-0 after:-z-10 after:rounded-full after:bg-teal-100 after:bg-opacity-0 after:blur-md;
  /* Hover styles */
  @apply transition-colors hover:border-teal-200/40 hover:text-teal-300 after:transition-all after:duration-500 after:hover:bg-opacity-15 after:animate-pulse focus:ring-2;
}
```

#### Build the footer

Copy the `AppHeader` and remove all `isOpen` code, styles, buttons, and leave nav, GlideLogo and ul. Make sure to update `aria-label` to Footer.

Programmatically add a screen reader only class to the GlideLogo (`{{ settings?.data.site_title }} home page` = Kentville Marlins home page).

### Adding Our Pages

In Slice Machine we go to **_Page Type_** (Not Custom Type). If you look at the default page created on Prismic you will see a **title**, which is Rich Text (Unlike the meta title in the custom type settings).

1. We add a new tab to the Page Type of **Page** (Right beside the Main tab) and name it **_SEO_**.
2. Click the + symbol and add **Text** and call it **_Meta Title_**.
3. Click + again and add **Text** and call it **_Meta Description_**.
4. Click + again and add **Image** and call it **_Meta Image_**. Also constrain the dimensions to 2400px by 1260px.
5. Push the saved changes in Slice Machine to Prismic by clicking **Review Changes** and clicking **Push**.

Now if we go to the Prismic Page Builder and click **Homepage** we will see a tab for **_SEO_**. On the SEO tab you can add metadata.

1. Click SEO tab and add in title, description, and image for the homepage.
2. Click **Save** and **Publish**.

We have a problem when we reload the page in dev that the metadata is not reflected. We need to update our **_page types_**.

1. Go to `/app/pages/index.vue` (Responsible for querying our page content).
2. Go back to Slice Machine > Page Types > Page > Click **_Page Snippet_** and grab the `useSeoMeta` snippet.
3. Within index.vue remove `useHead` and replace with the copied `useSeoMeta`.
4. Do the same as step 3, but in `/app/pages/[uid].vue`.

Now the metadata should show on the dev site.

### Prismic Slices

Slices are the sections of the pages.

You will see slices in Slice Machine. There should already be one there for **RichText** slice which was used as part of the homepage.

#### Hero Section Slice

1. Enter Slice Machine and click on **Slices**.
2. Click **Create** and enter **_Hero_** for the **Slice Name**.
3. You will then be brought to a page with variations and fields. Click on **Add a field**.
4. Add a **Rich Text** field, add **_Heading_** for the **Label**, select just h1 for **Accept**, and unselect **Allow multiple paragraphs**.
5. Add another **Rich Text** field, add **_Body_** for the **Label**, and select p/b/i for **Accept**.
6. Add a **Link** field for the CTA, add **_CTAs_** for the **Label**, and check **Make this link repeatable**.
7. Add an **Image** field and add **_Image_** for the **Label**.

Usually you would review changes and publish to Prismic, but with slices you could also click **Simulate**. This opens up a visual editor for slices.

> [!NOTE]
> If working in dark mode you can fix the white background on Simulate by going to `/app/pages/slice-simulator.vue` and add a background prop to `<SliceSimulator></SliceSimulator>` component (i.e. `background="#030712"`).

You can verify changes to the Slice Machine Simulator for the Hero by going to `/app/slices/Hero/index.vue` and updating the `<template></template>` section with `{{ slice }}` for example. This will display the JSON for this slice in the Simulator.

##### Templating Hero Slice

**_JavaScript Explanation_**

In `/app/slices/Hero/index.vue` we are defining our props and our slice hero component is receiving some props from the page (i.e. **slice**, **index** (array of slice from prismic which are the breakdown of sections of the page), **slices**, and **context** (arbitrary object you can paste to the SliceZone in `/app/pages/index.vue` to perform things on the slice such as storing global data)).

**_Templating_**

Looking at the design there is consistent padding/margin on x-axis for each slice.

1. Create a new component called `Bounded.vue`.
2. Inside the template we will render a `<Component />` from vue with the `as` prop or a `section` by default.
3. In the scripts we will `defineProps` as string and optional (`?`).
4. Render `<slot />` inside the `Component`.
5. Style the `Component` as centered and fixed max width.
6. Fix the error for "Components should always be multi-word" to eliminate conflicts. We will just bypass it this time in eslint config.
7. Back in the `Hero` component we will replace the section to the `Bounded` component we created.
8. Show snippets for hero slice in slice machine and copy each snippet into the `Hero` component replacing `{{ slice }}`.
9. Remove `PrismicRichText` for the heading and leave as just `PrismicText`. Then we add `wrapper="h1"` to have this set as an h1 element.
10. Do the same for the body text however we will use rich text later. Add `wrapper="p"`.
11. For the link (ctas) cut the attributes from the template and put it in the PrismicLink element. We only want to repeat the component and not the wrapper. Also wrap inside a div instead of template.
12. You can rename `v-for`, `key` and `field` to cta instead of link.
13. Create a class for the container of the image (glassContainer).
14. Add the splash of colour behind hero image:

```html
<div
  class="absolute left-1/3 top-0 -z-10 h-2/3 w-2/3 bg-teal-600/50 blur-3xl md:blur-[120px] filter mix-blend-screen"
/>
<div
  class="absolute left-0 top-1/3 -z-10 h-2/3 w-2/3 bg-sky-700/50 blur-3xl md:blur-[120px] filter mix-blend-screen"
/>
```

**_Animate Hero Template_**

First, within the hero slice we will call the `onMounted` composable.

Within the `onMounted` composable we will use a **_GSAP timeline_**. First create a timeline variable containing GSAP ease and power followed by `tl.fromTo(".hero__heading", { scale: 0.5, opacity: 0 }, { scale: 1, opacity: 1, duration: 1.4 });`. The second animates the scale from 0.5 to 1 with a duration of 1.4. As well as a timeline animation for the remaining hero sections.

For the image glow we will create it outside the timeline. One point is about these animations is the `repeat: -1` means that it will repeat infinite times.

```javascript
gsap.to(".hero__glow--one", {
  ease: "power2.inOut",
  repeat: -1,
  repeatDelay: 0,
  keyframes: [
    { top: "0%", left: "33%", duration: 0 },
    { top: "33%", left: "33%", duration: 2 },
    { top: "33%", left: "0%", duration: 3 },
    { top: "0%", left: "0%", duration: 2 },
    { top: "0%", left: "33%", duration: 3 },
  ],
});
```

Now we can disable animations for accessibility. We put the following code inside the `onMounted` composable:

```javascript
// For accessibility.
const prefersReducedMotion = window.matchMedia(
  "(prefers-reduced-motion: reduce)"
).matches;

if (prefersReducedMotion) {
  return;
}
```

**_Animated Grid Component_**

Create a new component within the `Glide` directory called `Grid.vue`. Within the component we will first render the grid then animate it. See `/app/components/Glide/Grid.vue`.

```vue
<script lang="ts" setup>
// Grid is 14 rows and 30 columns.
const grid = [14, 30];
</script>

<template>
  <svg
    id="glideGrid"
    xmlns="http://www.w3.org/2000/svg"
    fill="none"
    viewBox="0 0 935 425"
    class="absolute -left-2 -top-14 -z-10"
    style="mask-image: linear-gradient(black, transparent)"
  >
    <g class="glide-grid-group">
      <!-- Vue template for the vector path. -->
      <!-- The below d is rendering in absolute positions and we need to render it based on the position in the grid or i and j value and a relative path. -->
      <!-- FROM -->
      <!-- i.e. d="M3.19355 2.95082L5 0L0 2.95082L3.93548 4L3.19355 2.95082Z" -->
      <!-- TO -->
      <!-- :d="`M${(j - 1) * 32 + 5},${(i - 1) * 32 + 10}l1.806,-2.951l-5,2.951l3.936,1.049l-0.742,-1.049z`" -->
      <template v-for="i in grid[0]" :key="i">
        <path
          v-for="j in grid[1]"
          :key="j"
          fill="currentColor"
          opacity=".2"
          class="glide-grid-item"
          :d="`M${(j - 1) * 32 + 5},${(i - 1) * 32 + 10}l1.806,-2.951l-5,2.951l3.936,1.049l-0.742,-1.049z`"
        />
      </template>
    </g>
  </svg>
</template>
```

And for the animations:

```javascript
onMounted(() => {
  // For accessibility.
  const prefersReducedMotion = window.matchMedia(
    "(prefers-reduced-motion: reduce)"
  ).matches;

  if (prefersReducedMotion) {
    gsap.set("#glide-grid", { opacity: 1 });
    gsap.set(".glide-grid-item", {
      opacity: 0.2,
      scale: 1,
    });
    return;
  }

  // Starting point of animation.
  gsap.set(".glide-grid-item", {
    opacity: 0,
    transformOrigin: "center",
    color: "#fff",
  });
  gsap.set("#glide-grid", { opacity: 1 });

  // Define the timeline.
  const tl = gsap.timeline();

  // Entrance Animation.
  tl.to(".glide-grid-item", {
    keyframes: [
      { opacity: 0, duration: 0 },
      {
        opacity: 0.4,
        rotation: "+=180",
        color: "#0284c7",
        scale: 3,
        duration: 0.6,
        stagger: {
          amount: 2,
          grid: grid,
          from: "center",
        },
      },
      {
        opacity: 0.2,
        rotation: "+=180",
        color: "#fff",
        scale: 1,
        delay: -2,
        duration: 0.6,
        stagger: {
          amount: 3,
          grid: grid,
          from: "center",
        },
      },
    ],
  });

  // Loop Animation.
  tl.to(".glide-grid-item", {
    delay: 12,
    repeat: -1,
    repeatDelay: 12,
    keyframes: [
      {
        opacity: 0.4,
        rotation: "+=180",
        color: "#0284c7",
        scale: 3,
        duration: 0.6,
        stagger: {
          amount: 2,
          grid: grid,
          from: "center",
        },
      },
      {
        opacity: 0.2,
        rotation: "+=180",
        color: "#fff",
        scale: 1,
        delay: -2,
        duration: 0.6,
        stagger: {
          amount: 3,
          grid: grid,
          from: "center",
        },
      },
    ],
  });
});
```

##### Push Hero Slice to Prismic

Add a screenshot to the slice manager for the hero slice.

Then before we push to Prismic we need to do something that will allow us to add it to our **Page types**. Go to **Page types** > **Page** > **Add** > **Select existing** > Select the hero slice > **Add**.

Go to slice machine and select **Review changes** > **Push**.

Now if we go to Prismic (Page builder) and click on **Homepage** > **+** we will have the option of adding the hero slice.

[prismic]: https://prismic.io
[nuxt]: https://nuxt.com
[evan-dev]: https://www.evanmarshall.dev
[youtube-tut]: https://www.youtube.com/watch?v=EmvCh7Jb0Mw&t=307s
[nuxt-tailwind]: https://tailwindcss.nuxtjs.org/
[nuxt-fonts]: https://fonts.nuxt.com/
