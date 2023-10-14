---
title: "Updating Angular Applications to the Latest Version"
seoTitle: "angular update"
seoDescription: "angular update latest version cli command"
datePublished: Sat Oct 14 2023 06:35:53 GMT+0000 (Coordinated Universal Time)
cuid: clnpnywjq000c08lb9uguev7e
slug: updating-angular-applications-to-the-latest-version
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1697265242626/1f4bd1f3-0340-4f71-a12f-94a457b5302d.png
tags: angular, typescript, update, angularupdate

---

There are a few steps to update an Angular application to the latest version:

1. Make sure you have the latest Angular CLI installed. You can install it with:
    

```plaintext
npm install -g @angular/cli@latest
```

1. Update your Angular dependencies to the latest version. You'll need to update `@angular/core`, `@angular/cli`, and any other Angular libraries your app uses.
    

For example, to update to Angular 12, you would run:

```plaintext
ng update @angular/core@12 @angular/cli@12
```

1. Run `ng update` to update the Angular configuration files like `angular.json`.
    

```plaintext
ng update @angular/cli
```

1. Update any third-party dependencies to compatible versions. Some libraries may require version updates when updating Angular.
    
2. Make any necessary code changes. The Angular Update Guide can help identify any changes needed for your app.
    
3. Build and serve your application to test for any errors. Resolve any build errors or warnings.
    

```plaintext
ng build
ng serve
```

1. If needed, update from `HttpModule` to `HttpClientModule` and switch to pipeable RxJS operators.
    

Some other tips:

* Update to the latest Angular version as soon as possible to minimize required code changes.
    
* Keep a watch on deprecated features and plan changes ahead of time.
    
* Use the `--force` and `--allow-dirty` flags with `ng update` if needed.
    

Hope this helps! Let me know if you have any other questions.