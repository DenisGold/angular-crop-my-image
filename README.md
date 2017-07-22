# Angular Crop My Image

## Requirements

 - Modern Browser supporting ```<canvas>```

## Installing

### Download

- [Download angular-crop-my-image](https://github.com/AllanBishop/angular-crop-my-image/archive/master.zip) files from GitHub.

Or

- Install with Bower

```javascript
bower install angular-crop-my-image
```


### Add dependency

Add the image cropper module as a dependancy to your application module:
```javascript
angular.module('myApp', ['angular-crop-my-image']);
```

## Options


| Parameter | Description |
| ------ | ----------- |
| crop-width  | The width of the crop area|
| crop-height | The height of the crop area|
| image | The source image to crop|
| cropped-image | The cropped image|
| keep-aspect   | Enforces that the aspect ratio is kept when dragging the crop area. The aspect ratio is defined by the width and height paramater. |
| touch-radius  | The radius for detecting touches/clicks on the corner drag markers and the centre drag marker. |
| crop-area-bounds (*optional*) | A model that will be automatically updated with the bounds (left, right, top, bottom) of the crop area relative to the original source image.
| min-width (*optional*) | The minimum width that the crop area can be set to.
| min-height (*optional*) | The minimum height that the crop area can be set to.

## Example usage

#### Markup example

```html
<!DOCTYPE html>
<html>
<head>
<script src="https://ajax.googleapis.com/ajax/libs/angularjs/1.3.15/angular.js"></script>
<script src="angular-crop-my-image.min.js"></script>
<script>
    angular.module('myApp', ['angular-crop-my-image']);
    
    angular.module('myApp').controller("ImageCropperCtrl",[ '$scope', function($scope) 
    {
        $scope.cropper = {};
        $scope.cropper.sourceImage = null;
        $scope.cropper.croppedImage   = null;
        $scope.bounds = {};
        $scope.bounds.left = 0;
        $scope.bounds.right = 0;
        $scope.bounds.top = 0;
        $scope.bounds.bottom = 0;
    }]);
</script>
<meta charset="utf-8">
<title>Example</title>
</head>
<body ng-app="myApp">
    <div ng-controller="ImageCropperCtrl as ctrl">
        <input type="file" img-cropper-fileread image="cropper.sourceImage" />
        <div>
             <canvas width="500" height="300" id="canvas" image-cropper image="cropper.sourceImage" cropped-image="cropper.croppedImage" crop-width="400" crop-height="200" keep-aspect="true" touch-radius="30" crop-area-bounds="bounds"></canvas>
        </div>
        <div>Cropped Image (Left: {{bounds.left}} Right: {{bounds.right}} Top: {{bounds.top}} Bottom: {{bounds.bottom}})</div>
        <div ng-show="cropper.croppedImage!=null"><img ng-src="{{cropper.croppedImage}}" /></div>
    </div>
</body>
</html>
```


## License

See the [LICENSE](https://github.com/AllanBishop/ImageCropper/blob/master/LICENSE.md) file.
