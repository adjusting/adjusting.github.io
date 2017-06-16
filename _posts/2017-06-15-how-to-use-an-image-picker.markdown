---
layout: post
title:  "How to Use an Image Picker"
date:   2017-06-15
categories: uikit xcode
---

- Drag an image view into your UI
- Add an outlet to your view controller:

```swift
	@IBOutlet weak var imageView: UIImageView!
```

- Drag from the view controller to the image view to connect the outlet
- Drag a button into your UI
- Add an action to your view controller:

```swift
	@IBAction func pickAnImageFromCamera(_ sender: Any) {
        let sourceType: UIImagePickerControllerSourceType = .photoLibrary
        // Replace .photoLibrary by .camera if you'd rather take a new picture
        // instead of getting it from the photo library
        let imagePicker = UIImagePickerController()
        imagePicker.delegate = self
        imagePicker.sourceType = sourceType
        present(imagePicker, animated: true, completion: nil)
    }
````

- Drag from the view controller to the button to connect the action
- Add the following extension to the same file as your view controller:

```swift
extension ViewController: UIImagePickerControllerDelegate {

    func imagePickerControllerDidCancel(_ picker: UIImagePickerController) {
        picker.dismiss(animated: false, completion: nil)
    }
    
    func imagePickerController(
    	_ picker: UIImagePickerController, 
    	didFinishPickingMediaWithInfo info: [String : Any]) {

        if let image = info[UIImagePickerControllerOriginalImage] as? UIImage {
            imageView.image = image
        }
        picker.dismiss(animated: false, completion: nil)
    }

}
```
