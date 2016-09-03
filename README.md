# Best Practices for Structuring An Angular App

If you are contemplating building an application with Angular, you might be giving some thought to how to structure your codebase so it's readable and maintainable. You essentially have to think about the nuts and bolts of Angular, namely controllers, components/directives, factories, templates, and services.

In general, there are a couple of approaches you can take. I present each of these approaches in To-Avoid.md and To-Follow.md. As the filenames imply, I strongly urge to avoid the first approach and recommend following the second.

## The Approach to Avoid

The first approach is based on separation of concerns, where core Angular features have their own directories. This means that you have top-level directories for controllers, components/directives, factories, templates or views, and services.

This approach has a not-too-obvious problem, depending on your experience working with Angular. The problem is that discrete page units cannot be deciphered from this structure. 

If you have, for example, a particular widget on a particular page in your application, you cannot simply tell all it's related files from this structure. 

You basically end up being forced to name your controller, component/directive, etc. after your widget and having to go to each of those directories to figure out if there's something related to the widget in those core feature directories. 

The end result is a bad user experience for developers, who end up having to navigate your codebase to find things.

## The Approach to Follow

The second approach is based on tightly coupling discrete page units. Instead of top-level directories for core Angular features, let the application's user-facing taxonomy drive the directory structure.

What does this mean?

First, think about the IA (Information Architecture) of your application and draw it out. Let's use an example to explain this. 

We want to build a content management system for people to create and edit content. You need some kind of content index or indices and pages with edit forms to allow the content to be created and edited.

So you create top-level directories for indices and edit forms. Now, you know that some functionality will be shared across these pages, so create a top-level "common" or "shared" directory.

Under each of these, you can start creating sub-directories for meaningful pages or page units. Perhaps under edit forms, you can create "article," "gallery," and so on, and under indices you can either create sub-directories for each kind of index you are going to build or just drop index.* files if you're dealing with a single content index.

Under "common" or "shared," it might make sense to create directories for core Angular features, e.g. components/directives, factories, and services. 

Many projects I've come across don't rely enough on the concept of modules. Modules exist so you can break up your code into small yet reasonable pieces. When this idea isn't leveraged enough, what you end up with is bloat, single files that include code for controllers, components/directives, services, etc.

Knowing you can leverage modules to break up your code, under each sub-directory, it might make sense to create further sub-directories for core Angular features. So under editForms/article, you might have directories named "components," "partials," "factories," and "services," as needed.

Furthermore, you might also create subdirectories under each of these for bundles of files. For example, under "components," you might want to create subdirectories for widgetA, widgetB, and so on, assuming those aren't just made up of a single file. In some cases, those might even have subdirectories for core Angular features. I tend to follow the practice of having an index.js file inside each such subdirectory to indicate a logical starting point.

In summary, it's always best to have your directory structure mean something. It makes it easier to navigate and understand for other users. It also makes it easier to maintain and be used by larger teams.
