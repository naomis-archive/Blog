## Lighthouse

Did you know that Google offers a free, open-source tool for checking various analytics on your web page? That tool is called [Lighthouse](https://developers.google.com/web/tools/lighthouse), and today we are going to talk about what it has to offer. 

## What is Lighthouse?

Lighthouse is an analytics tool that measures various aspects of your webpage. It checks your page for performance, accessibility, best practises, search engine optimisation, and a progressive web app (if applicable). What is *most* important about these metrics is that Google uses them to help determine search result rankings. The higher your metrics, the more likely your site is to show up in a Google search result. 

## How do you use it?

There are a few options for utilising this helpful tool. Google Chrome offers Lighthouse analysis built in as part of the Chrome Dev Tools, and there is an `npm` package available as well. However, my preferred method is with a GitHub action. This GitHub action will analyse your page when you open a pull request, so you can see the results of your changes *before* you merge to your production branch. This helps ensure that any additions or modifications do not negatively impact your website rankings. 

## Setting up GitHub Actions

There are a couple of steps you will need to take to get this workflow configured properly. If you have not used a GitHub action before, you can refer to the [GitHub documentation]() for additional information. 

The first step is to set up your Lighthouse configuration. In the *root* directory of your project, add a file called `lighthouserc.js` and paste the following code into it: 

```js
module.exports = {
  ci: {
    collect: {
      staticDistDir: './',
    },
    upload: {
      target: 'temporary-public-storage',
    },
  },
};
```

This code will determine where your lighthouse integration will read the static files from (the `staticDistDir` setting). In our case, it will read from the root folder (if you are using a webpack, you might change this to your `build` folder, for example). The code also determines where to upload the temporary reports that get sent to the Lighthouse tools. I would not recommend changing that setting. 

Next, we will need to create the action workflow. In your root directory, ensure there is a `.github` folder (this folder contains workflows, issue templates, pull request templates, and the CODEOWNERS file). Within that folder, look for the `workflows` folder (this folder contains your GitHub actions files). Inside that folder, create a file called `lighthouse-ci.yml` and paste the following code into it:

```yaml
name: CI
on: [pull_request]
jobs:
  lighthouseci:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Setting up environment
        uses: actions/setup-node@v1
      - name: Run LightHouse CI
        run: |
          npm install -g @lhci/cli@0.4.x
          lhci autorun
        env:
          LHCI_GITHUB_APP_TOKEN: ${{secrets.LHCI_GITHUB_APP_TOKEN}}
```

This code will set up the environment and run the lighthouse integration on the codebase for every pull request.

## Report

Upon completion of the CI, you will be able to view reports for your HTML pages. If you look at the lighthouse-ci check, you can get to a screen that looks like this: 

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598726745629/-7KHGdON8.png)

You will want to select the "Run Lighthouse CI" details, scroll down to the bottom, and find the report links. Copy each one and paste it into the URL box of your browser (use new tabs - it's helpful!). When the page loads, you should see something like this:

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1598726985722/rDC8C7hvi.png)

Great! Let's talk about these!

### Performance

The performance metric measures how quickly your page loads. Things like external CSS and JS sources, large images, and unnecessary styles/scripts will negatively impact this score. 

### Accessibility

The accessibility metric measures how compatible your site is with things like screen readers. Having improperly ordered elements, missing meta information, and hiding elements from screen readers will negatively impact this score. 

### Best Practises

The best practises metric measures how well you follow various internet standards. Using HTTP instead of HTTPS, requesting location/notification permissions, and missing meta information will negatively impact this score. 

### Search Engine Optimisation

The SEO metric measures how well your page is optimised for search engine crawlers. Missing meta information, missing img alt text, and poor mobile responsiveness will negatively impact this score. 

## What's next?

The report will give you specific feedback for any opportunities your page has, as well as links to Google documentation on how to correct these opportunities. The documentation is rather vague, as it applies to the overall concept instead of your specific opportunity, so you may need additional research. With your GitHub action integration, however, you can apply changes and push them to your PR branch and Lighthouse will automatically generate new reports!