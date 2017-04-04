---
layout: post
title:  "Three Ways to Transition Between Views"
date:   2017-04-03
categories: uikit segue
---
# Code only
~~~~ swift
@IBAction func transition() {

        let controller: NewViewController
        controller = storyboard?.instantiateViewController(
        	withIdentifier: "NewViewController") as! NewViewController

        // Pass information to the new controller

        present(controller, animated: true, completion: nil)
}
~~~~

<br/>

# Code and Segue
- control-drag from one view controller to the other to set up the segue
- set the segue identifier in the segue’s attribute inspector

~~~~ swift
@IBAction func transition(){
      performSegue(withIdentifier: "mySegue", sender: self)
}

override func prepare(for segue: UIStoryboardSegue, sender: Any?) {

    if segue.identifier == "mySegue" {
        let controller = segue.destination as! NewViewController

        // Pass information to the new controller
    }
}
~~~~

<br/>

# Segue only
- control drag from the button to the new view controller to set up the segue
- set the segue identifier in the segue’s attribute inspector

~~~~ swift
override func prepare(for segue: UIStoryboardSegue, sender: Any?) {

    if segue.identifier == "mySegue" {
        let controller = segue.destination as! NewViewController

        // Pass information to the new controller
    }
}
~~~~


