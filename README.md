# Hashem, Image CRUD In One Line
 [![Issues](https://img.shields.io/github/issues/BNhashem16/Images.svg?style=plastic&logo=appveyor)](https://github.com/BNhashem16/Images)

[![Forks](https://img.shields.io/github/forks/BNhashem16/Images.svg?style=plastic&logo=appveyor)](https://github.com/BNhashem16/Images)

[![Stars](https://img.shields.io/github/stars/BNhashem16/Images.svg?style=plastic&logo=appveyor)](https://github.com/BNhashem16/Images)

[![License](https://img.shields.io/github/license/BNhashem16/Images.svg?style=plastic&logo=appveyor)](https://github.com/BNhashem16/Images)

[![Twitter](https://img.shields.io/twitter/url?url=https%3A%2F%2Fgithub.com%2FBNhashem16%2FImages)](https://github.com/BNhashem16/Images)

## Installing Hashem

The recommended way to install Hashem is through
[Composer](https://getcomposer.org/).

```bash
composer require ahashem/image
```

## Storage Link

Creating Shourtcut of storage folder , you will found shortcut by following this path `your-project/public`

```bash
php artisan storage:link
```

## Updating your Provider Array

you should Go to `config\app.php` , in Provider array you should put this Line:

```php

'providers' => [
        /*
         * Laravel Framework Service Providers...
         */
        Hashem\Image\ImageServiceProvider::class,
    ],
```

## Store Image

```php
    use Hashem\Image\Traits\Image;


    public function store(Request $request)
    {
        $post = new Post([
            'image' => Image::store('pages' , 'image'),
            'banner' => Image::store('pages' , 'banner'),
        ]);
        $post->save();

        // pages is the parent Folder 
        // image and banner is the childs Folders
        // image and banner also request name , that mean image or banner is required.
    }

```


## Update Image

In update Model function: 
- If `$request->image` or `$request->banner` is Equal null , that mean Nothing Will Not happen
- If `$request->image` or `$request->banner` is Not Equal null , that mean image or banner will removed from Database and Server and store New image that will comming From request 

```php
    use Hashem\Image\Traits\Image;


    public function update(Request $request , Post $post)
    {
        $post->update([
            'image'  = Image::update('pages' , 'image' , $post),
            'banner' = Image::update('pages' , 'banner' , $post),
        ]);

        // pages is the parent Folder 
        // image and banner is the childs Folders
        // image and banner also request name , that mean image or banner is required.
        // You should pass Row to function
    }

```

## Destroy Image

In destroy Model function: Image will removed From Database and also will Removed from server.

```php
    use Hashem\Image\Traits\Image;


    public function destroy(Request $request , Post $post)
    {
        Image::destroy('image' , $post);
        Image::destroy('banner' , $post);

        // You should pass Row to function
    }

```
