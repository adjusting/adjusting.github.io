---
layout: post
title:  "How to Use a Textfield Delegate"
date:   2017-04-16
categories: uikit xcode
---

- Drag a textfield into your UI
- Add an outlet to your view controller:

```swift
    @IBOutlet var textField1: UITextField!
```

- Drag from the view controller to the textfield to connect the outlet
- Create a new swift file and add the following code:

```swift
import Foundation
import UIKit

class MyNewDelegate: NSObject, UITextFieldDelegate {
    func textField(_ textField: UITextField, shouldChangeCharactersIn range:
    NSRange, replacementString string: String) -> Bool {
        
// Make any desired modifications to the textField's properties (e.g. text,
// textColor, font, etc)
// return true to append replacementString, false otherwise

        return true
    }
}
```

- Edit your view controller to include the following code:

```swift
    let myDelegate = MyNewDelegate()

    override func viewDidLoad() {
        super.viewDidLoad()
        textField1.delegate = myDelegate
    }
```
