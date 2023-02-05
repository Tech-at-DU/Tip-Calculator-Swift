# Implementing Subviews

In the previous section, we implemented a skeleton of each of the UI groups in storyboard. If you build and run your project, your app should look like the following:

![Finished UI Skeleton](assets/finished_ui_groups.png)

In this section, you will finish building each of our _view groups_:

1. Header
2. Tip Input Card
3. Tip Output Card
4. Reset Button

To finish implementing each of the _view groups_, you need to the process below:

1. Add each of the correct `UIKit` objects
2. Identify and set _auto-layout_ constraints for each subview
3. Configure each subview's attributes to match the designs
4. Create the appropriate `IBOutlets` and `IBActions`

# Header View

In the previous step, you added a base view (`UIView`) for the header. In it's current state, our header view looks like this:

![Current Header View](assets/current_nav_bar.png)

To finish implementing the header view, you need to identify and add the remaining subviews.

> [challenge] Using the design below, can you identify the views we'll need to finish building the UI for our header view?

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

![Header View Design](assets/nav_bar_design.png)

<!-- break -->

> [solution] You need the following view objects to build our header:
>
> - `UILabel`: title label
> - `UISwitch`: theme color switch

After identifying both of the view objects we'll need to add, we'll need to add them as a subview and set each of their respective constraints.

## Title Label

### Identifying Constraints

Before adding constraints in storyboard, take a step back and think of all the constraints  needed for the title label.

> [challenge] Using the design below, identify each of the _auto-layout_ constraints for your title label. Write each of the constraints down on a sheet of paper.
>
> **Hint:** the red area represents the frame of the label.

![Header View Label Dimensions](assets/nav_bar_label_dimensions.png)

Check your answer with the solution below.

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-


> [solution] Based on our design, our label will need the following constraints:

![Header View Label Constraints](assets/nav_bar_label_constraints.png)


**Constraints**:
- (Label) Leading Edge 24pts from Super View (Header View) Leading Edge
- (Label) Bottom Edge 0pts from Super View Bottom Edge
- (Label) Top Edge 0pts from Safe Area Top Edge

### Adding Constraints

After identifying our constraints, use _Interface Builder_ to add a new `UILabel` and apply constraints.

> [action] Open `Main.storyboard` and implement your title label and it's constraints:
>
> Step-by-step:
>
> 1. Drag a `UILabel` from the _Object Library_ and drop it on top of your header view (`UIView`). It should be a child of the header view. You can check this in the outline view on the left side. 
> 2. With your new `UILabel` selected, click the `Add New Constraints` button.
> 3. Add the following first two constraints using the `Add New Constraints`. 
    - (Label) Leading Edge 24pts from Super view
> 4. Click the align menu (to the left of the Add constraints button) check `Vertically in container`. This aligns the label in the vertical center of it's container.  

![ms-video](assets/add_nav_bar_label_w_constraints.gif)

<!-- break -->

> [info] Identifying and setting the _auto-layout_ constraints for each view object can be tricky. If you find yourself struggling, slow down and try to break down your layout problem into smaller chunks. As you continue to practice, working with constraints will become easier and easier.

Nice! We've added a title label to our header. If you build and run your project, you'll see the following:

![Header Title Label Without Styling](assets/nav_bar_label_no_styling.png)

But... it's still off. Our title label still doesn't look like our final design.

### Configuring Attributes

> [action] In `Main.storyboard`, select your header view's title label. Navigate to the _Attributes Inspector_ in the _Utilities area_ and change the following attributes:
>
> - _Text_: Change from `Label` to `Tip Calculator` ![Set Header View Label Text](assets/set_nav_bar_label_text.png)
> - _Font_: Change from `System 17.0` to `System Bold 24.0` ![Set Header View Label Font](assets/set_nav_bar_label_font.png)
> - _Font Color_: Use the blue dropdown to change from `Default` to `tcCharcoal` ![Set Header View Text Color](assets/set_nav_bar_label_text_color.png)

After configuring each of the attributes above, your title label should look like the following:

![Header View Label Styled](assets/nav_bar_label_w_styling.png)

Looks pretty good huh? Let's move on to our `UISwitch`.

## Light/Dark Mode (Theme) Switch

Identify constraints. Add object and set constraints. Configure attributes. Rinse. Repeat.

You are going to repeat this process many times before this tutorial is over. Get comfortable with this, as it's the same process you'll need to use if when you're building your own apps.

Let's start by identifying the constraints needed for our `UISwitch`.

### Identifying Constraints

> [challenge] Using the design below, identify each of the _auto-layout_ constraints for your theme switch. Write each of the constraints down on a sheet of paper.
>
> Hint: the red area represents the frame of the switch.

![Header View Switch Dimensions](assets/nav_bar_switch_dimensions.png)

Check your answer with the solution below.

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

> [solution] Based on our design, our `UISwitch` will need the following constraints:
>
![Header View Switch With Constraints](assets/nav_bar_switch_constraints.png)
>
**Constraints**:
>
> - (Switch) Trailing Edge 24pts from Super View (Header View) Trailing Edge
> - (Switch) Leading Edge ≥20pts from Label Trailing Edge
> - (Switch) Center vertically aligned with Label Center

### Adding Constraints

Go ahead add a `UISwitch` and add these constraints.

> [action] Open `Main.storyboard` and implement your `UISwitch` and it's constraints:
>
> Step-by-step:
>
1. Drag a `UISwitch` from the _Object Library_ and drop it "into" to your header view.
2. With your  `UISwitch` selected, click the `Add New Constraints` button.
3. Add the following two constraints using the `Add New Constraints` popup:
    - (Switch) Trailing Edge 24pts from Super View Trailing Edge
4. Click the Align button (to the left of Add Constraints) and check "Vertically in container"

![ms-video](assets/add_switch_w_constraints.gif)

Nice! you added and set the constraints to space the `UISwitch` from the left edge and align it vertically in it's parent view. Now,configure the switch's attributes.

### Configuring Attributes

> [action] In `Main.storyboard`, select your header view's switch. Navigate to the _Attributes Inspector_ in the _Utilities area_ and change the following attributes:
>
![Switch Attributes](assets/switch_attrs.png)
>
**Attributes:**
>
- _State_: Change from `On` to `Off`
- _On Tint_: Change from `Default` to `tcSeafoamGreen`

When you're done, your custom header view should look like the following:

![Header View With Styling](assets/nav_bar_w_styling.png)

## Adding Our IB Connections

Almost finished with implementing the first UI group! To finish up, you need to create `IBOutlets` and `IBActions`.

`IBOutlets` and `IBActions` allow our Swift code receive events and interact with our storyboard views.

`IBOutlets` create an instance variable that can be referenced in Swift code. This way you can control UI elements created in storyboard. 

`IBActions` create a function that will execute code when triggered. These functions are triggered by user interaction with your UI elements. A common example is a user tapping a button. When the button is tapped, it triggers an `IBAction` that will run any code within it's corresponding function.

You need both of these connections to implement the tip calculator logic.

Get started by creating our first `IBOutlet` for our header view (`UIView`).

> [action] Open your `Main.storyboard` and `ViewController.swift` files side-by-side using the _Assistant Editor_:
>
> To create IB connections, we'll need to first open our storyboard and view controller source code side-by-side:
>
> 1. Open your `Main.storyboard` in your main editor.
> 2. Hold down the option button and click on `ViewController.swift` file in your _Project Navigator_. This will open your view controller in your _Assistant Editor_.
> 3. (Optional) Use your Xcode toolbar to hide the _Utilities area_ to create more space in your project.

![ms-video](assets/using_assistant_editor.gif)

With our `Main.storyboard` and `ViewController.swift` files side-by-side, create an `IBOutlet` for our header.

> [action] Create an `IBOutlet` for your header called `headerView`:
>
> Step-by-step:
>
> 1. Select your header view (`UIView`) in the _Document Outline_.
> 2. With your header view selected, hold down ctrl and click-drag from the header view in your _Document Outline_ to your Swift code within the `ViewController` class definition.
> 3. You should see a popup for creating a new IB connection. Set the name field as `headerView`.
> 4. Click _Connect_ to create your new `IBOutlet`.

![ms-video](assets/header_view_iboutlet.gif)

You should see a new `IBOutlet` instance variable in your `ViewController` class:

```Swift
class ViewController: UIViewController {

  @IBOutlet weak var headerView: UIView!

  // MARK: - View Lifecycle

  override func viewDidLoad() {
    super.viewDidLoad()
  }
}
```

With new variable you can now reference the header view as `headerView` in your Swift code.

Awesome! Repetition is the mother of learning. Let's do it again.

> [action] Create an `IBOutlet` for your header view's title label called `titleLabel`:
>
> Step-by-step:
>
1. Select your title label (`UILabel`) in your storyboard view controller.
1. With your Tip Calculator label selected, hold down ctrl and click-drag from the label to your Swift code within the `ViewController` class definition.
1. You should see a popup for creating a new IB connection. Set the name field as `titleLabel`.
1. Click _Connect_ to create your new `IBOutlet`.

![ms-video](assets/title_label_iboutlet.gif)

<!-- break -->

> [info] You can also create an `IBOutlet` by control dragging from the object in the storybaord mock up. 

At this point, we've walked through creating an `IBOutlet` twice. It's your turn.

> [challenge] Create an `IBOutlet` for your `UISwitch` named `themeSwitch`. If you get stuck, go back and reference the steps we used to create the previous two `IBOutlets`.

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

<!-- break -->

> [solution] After creating an `IBOutlet` for your switch, your `ViewController.swift` file should look like the following:


```Swift 
class ViewController: UIViewController {

    @IBOutlet weak var headerView: UIView!
    @IBOutlet weak var titleLabel: UILabel!
    @IBOutlet weak var themeSwitch: UISwitch!

    // MARK: - View Lifecycle

    override func viewDidLoad() {
        super.viewDidLoad()
    }
}
```

After checking your solution, let's move on to creating our first `IBAction`.

Create an `IBAction` for the switch. This will allow you to execute code each time the switch is toggled from off to on and vice versa.

> [action] Open both your `Main.storyboard` and `ViewController.swift` file using the _Assistant Editor_. Create a new `IBAction` for your switch:
>
> Step-by-step:
>
> 1. Select your switch (`UISwitch`) in the _Document Outline_.
> 2. With your switch selected, hold down ctrl and click-drag from the switch in your _Document Outline_ to your `ViewController` class.
> 3. You should see a popup for creating a new IB connection. In the popup, change the _Connection_ type from `Outlet` to `Action`. Changing this property allows us to create a different type of IB connection.
> 4. Set the name of our action as `themeToggled`.
> 5. Change the _Type_ property from `Any` to `UISwitch`.
> 6. Make sure the _Event_ property is set as `Value Changed`. If not, use the dropdown to set it to `Value Changed`.
> 7. Click _Connect_ to create your new `IBAction`.


![ms-video](assets/switch_ibaction.gif)

<!-- break -->

> [info] After creating your switch's `IBAction`, you can close the _Assistant Editor_. If don't have a lot of screen space, it's helpful to open and close the _Assistant Editor_ as you need it.

Give our new `IBAction` a test run to see that it's working correctly.

> [action] Open `ViewController.swift` from your _Project Navigator_ and add the following code in your `themeToggled` function:

```Swift
@IBAction func themeToggled(_ sender: UISwitch) {
  if sender.isOn {
    print("switch toggled on")
  } else {
    print("switch toggled off")
  }
}
```

After adding the code above we can test our `IBAction`.

> [action] Build and run your project. Toggle your switch on and off a couple of times. If you look at your Xcode _Debugger area_ you should see the following print statements in your console each time you toggle your switch:

![Switch Console Print](assets/switch_console_print.png)

You've finished implementing the UI and IB connections for the header view. Side-by-side, your `Main.storyboard` and `ViewController.swift` files should look like the following:

![Finished Header Project Snapshot](assets/finished_header_project_snapshot.png)

If you build and run your project, you app should look like:

![Finished Header App Snapshot](assets/finished_header_app_snapshot.png)

If you're looking for more practice, good news! We'll need to repeat the same steps again for our input card, output card and reset button views. Onwards!

> [info] As you get more advanced, you'll learn about creating custom view objects that abstract all of it's subview components. Creating custom views makes your custom views re-usable and decouples your code. 

# Input Card View

The next UI group you will complete is the input card. Let's take another look at our design:

![Input Card Design](assets/input_card_design.png)

The input card needs the following UI components:

![Tip Input Subviews](assets/tip_input_subviews.png)

The input card needs two labels, a text field, and a segmented control. Think about how to use _auto-layout_ to build this design.

## Identifying Constraints

To build our header view, you used constraints to create our dynamic view layout. This time, you you will use a new tool called `UIStackView`.

### Stack Views

`UIStackView` allows you to create a horizontal or vertical stack of views. This is especially useful for easily organizing rows or column layouts.

Take a look at what that looks like:

![Horizontal and Vertical Stack Views](assets/hor_and_ver_stack_views.png)

In both cases, you can see that each stack view contains multiple subviews. The `UIStackView` automatically handles calculating the frame of each subview within it.

Use stack views to easily layout subviews without having to add constraints.

Look at how you will use a horizontal stack view to group our first row of views.

![Bill Amount Stack View](assets/bill_amount_stack_view.png)

As you can see, both the _Bill Amount Title Label_ and _Bill Amount Text Field_ are added to a single `UIStackView`. The purple area in the image above shows the stack view's frame.

Similarly, you can use another horizontal stack view to layout the _Tip Percent Title_ and _Tip Segmented Control_ subviews. Let's look at what the would look like:

![Tip Percent Stack View](assets/tip_percent_stack_view.png)

Each `UIStackView` calculates the frame of each subview within it. However, you still need to somehow define the frame of each `UIStackView`.

To position both of our horizontal stack views in the center of your input card, you will apply constraints to the stack views. 

First, you will add a vertical stack view containing both horizontal stack views:

![Outer Stack View](assets/outer_stack_view.png)

Next, use constraints to dynamically center the outer stack view:

![Outer Stack View Constraints](assets/outer_stack_view_constraints.png)

We add the following constraints to the outer stack view:

- (Outer Stack View) Leading Edge 22pts from Super View (Input Card) Leading Edge
- (Outer Stack View) Trailing Edge 22pts from Super View Trailing Edge
- (Outer Stack View) Center vertically aligned with Super View Center

You need to add a few more width constraints to guarantee each view is of the correct width.

Start by adding an equal width to both inner (horizontal) stack views:

![Input Card Equal Widths Constraints](assets/input_card_equal_widths.png)

In the image above, we add the following two constraints:

- (Inner Top Stack View) Equal Width to Outer Stack View Width
- (Inner Bottom Stack View) Equal Width to Outer Stack View Width

As the name suggests, these two _Equal Widths_ constraints define the widths of the inner stack view to be the same as the outer stack view.

Last, we need to add a width constraint for our `UITextField` and `UISegmentedControl` respectively.

![Input Card Input Width Constraints](assets/input_card_input_width_constraints.png)

Our width constraints:

- (Bill Amount Text Field) 118pts Width
- (Tip % Segmented Control) 173pts Width

Whew! Those are the final constraints we'll need for our input card.

As you can see, the combination of stack views and constraints give developers a lot of power to create complex UI layouts.

Now that we've figured how we're going to implement the layout for our input card, let's start building!

## Adding Constraints

As you can see, the layout for our input card is pretty complex. To make things easier, we'll break our implementation into smaller steps.

We'll start with the inner top stack view: the _Bill Amount Stack View_.

### Bill Amount Stack View

First, add the stack view's sub-elements.

> [action] In `Main.storyboard`, add an `UILabel` and `UITextField` to your view controller:
>
> Step-by-step:
>
> 1. Drag a `UILabel` from the _Object Library_ and drop it on top of your input card view (`UIView`).
> 2. Drag a `UITextField` from the _Object Library_ and position it next to your previous label.
> 3. Make sure both subviews are positioned horizontally side-by-side. This will be important when we create our stack view.

![ms-video](assets/add_bill_amount_subviews.gif)

Next, create your first `UIStackView` from our two new views.

> [action] Create the _Bill Amount Stack View_ using the label and textfield:
>
> 1. Select your _Bill Amount Title Label_ (`UILabel`) in your storyboard.
> 2. Hold down shift and click on your `UITextField`. This allows you to select multiple items at the same time.
> 3. With both label and text field selected, click on the `Embed In` button near the `Add New Constraints` button. It's located in the bottom right corner of your _Editor area_.
> 4. (Optional) If you look in your _Document Outline_, you can see your new `UIStackView`. If you expand your stack view in your _Document Outline_ you can see each of the stack view's subviews.

![ms-video](assets/create_bill_amount_stack_view.gif)

Your storyboard should look like the following:

![Bill Amount Stack View Unstyled](assets/bill_amount_stack_view_unstyled.png)

Needs some work huh? We won't worry about the styling yet. Let's move onto creating the inner bottom stack view.

### Tip Percent Stack View

Add the _Tip Percent Stack View's_ subviews.

> [action] In `Main.storyboard`, add an `UILabel` and `UISegmentedControl` to your view controller:
>
> Step-by-step:
>
> 1. Drag a `UILabel` from the _Object Library_ and drop it below the first label.
> 2. Drag a `UISegmentedControl` from the _Object Library_ and position it so that it's next to the new label and below the text field.
> 3. Make sure both label and segmented control are positioned horizontally side-by-side. In addition, make sure that they're positioned below the previous stack view.

![ms-video](assets/add_tip_percent_subviews.gif)

Create our second inner stack view.

> [action] Create the _Tip Percent Stack View_ using the label and segmented control:
>
> 1. Select your _Tip Percent Title Label_ (`UILabel`) in your storyboard.
> 2. Hold down shift and click on your `UISegmentedControl`. This allows you to select multiple items at the same time.
> 3. With both label and segmented control selected, click on the `Embed In Stack` button near the `Add New Constraints` button. It's located in the bottom right corner of your _Editor area_.
> 4. (Optional) If you look in your _Document Outline_, you can see your new `UIStackView`. If you expand your stack view in your _Document Outline_ you can see each of the stack view's subviews.

![ms-video](assets/create_tip_percent_stack_view.gif)

Your storyboard should look like the following:

![Tip Percent Stack View Unstyled](assets/tip_percent_stack_view_unstyled.png)

Both stack views are still unstyled. You will get to that once we finish adding all our constraints.

Next, let's create our outer stack view.

### Outer Stack View

> [action] Create the _Outer Stack View_ using both inner (horizontal) stack views:
>
Step-by-step:
>
> 1. Collapse both inner stack views in the _Document Outline_.
> 2. Select any inner stack view in the _Document Outline_.
> 3. With the previous inner stack view selected, shift-click the other inner stack view to select both inner stack views simultaneously.
> 4. With both inner stack views selected, click on the `Embed In Stack` button.
> 5. (Optional) If you look in your _Document Outline_, you can see your new outer stack view and it's subviews.

![ms-video](assets/create_outer_stack_view.gif)

Your storyboard should now look like the following:

![Outer Stack View Unstyled](assets/outer_stack_view_unstyled.png)

With the inner and outer stack view constraints created, you need to add a few more constraints so _auto-layout_ can determine each stack view's frame.

Start with remaining outer stack view constraints.

> [action] Set the outer stack view's frame with the following constraints:
>
> Step-by-step:
>
> 1. Select the outer stack view in the _Document Outline_.
> 2. With your outer stack view selected, click the `Add New Constraints` button.
> 3. Add the following two constraints using the `Add New Constraints` popup:
    - (Outer Stack View) Leading Edge 22pts from Super View (input card) Leading Edge
    - (Outer Stack View) Trailing Edge 22pts from Super View Trailing Edge
> 4. In the _Document Outline_, hold down control (ctrl) and click-drag from the outer stack view to it's super view (input card).
> 5. In the popup, select `Center Vertically In Container` to create a new constraint. This will vertically align the outer stack view's center with it's super view's center.

![ms-video](assets/add_outer_stack_view_constraints.gif)

To make sure the outer and inner stack views are equal you need a couple more constraints. 

### Equal Widths Constraints

> [action] Set equal widths constraints for each stack view:
>
> Step-by-step:
>
> 1. Collapse both inner stack views in the _Document Outline_.
> 2. Select the outer stack view in the _Document Outline_.
> 3. With the outer stack view selected, shift-click the bottom inner stack view to select all three stack views simultaneously.
> 4. With all stack views selected, click the `Add New Constraints` button.
> 5. Select the `Equal Widths` checkbox and click `Add 2 Constraints` to create your equal width constraints.

![ms-video](assets/add_stack_view_equal_widths_constraints.gif)

Our progress so far:

![Stack View Equal Widths Unstyled](assets/stack_view_equal_widths_unstyled.png)

### Fixed Width Constraints

> [action] Set a width constraint for the _Bill Amount Text Field_:
>
> Step-by-step:
>
> 1. Select the `UITextField` object in the _Document Outline_.
> 2. With the text field selected, click the `Add New Constraints` button.
> 3. Set a fixed width constraint of 118pts.

![ms-video](assets/text_field_width_constraint.gif)

Finally, add a fixed width constraint to the `UISegmentedControl`. Try to see if you can implement it by yourself.

> [challenge] Add a width constraint for your _Tip Percent Segmented Control_ object. Set the width to 173pts. If you have trouble or get stuck, look at the previous example of adding a width constraint to our text field.

Check your solution below.

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

> [solution] We set a width constraint for our _Tip Percent Segmented Control_ with the following:
>
Step-by-step:
>
> 1. Select the `UISegmentedControl` object in the _Document Outline_.
> 2. With the segmented control selected, click the `Add New Constraints` button.
> 3. Set a fixed width constraint of 173pts.

![ms-video](assets/segmented_control_width_constraint.gif)

This has come a long ways from where you first started. You've finished adding all of your stack views and each view's constraints.

![Input Card Finished Constraints Unstyled](assets/input_card_finished_constraints_unstyled.png)

As you can see, the input card is starting to look more and more like the design. Next, work on configuring the input card view attributes.

## Configuring Attributes

At this point, you should be familiar with setting the attributes of a storyboard object using _Interface Builder_.

We'll quickly go through one together for review and let you do the rest on your own.

### Input Card Background Color

> [action] Set the _Input Card's_ background color to `tcDarkBlue`:
>
Step-by-step:
>
> 1. Select the input card view (`UIView`).
> 2. Open the _Attributes Inspector_ in the _Utilities area_.
> 3. Find the _Background_ attribute and use the blue dropdown button to change it's value from `White Color` to `tcDarkBlue`.

![ms-video](assets/set_input_card_bg_color.gif)

Now it's your turn.

> [challenge] Set each of the following attributes for each respective element:
>

**Outer Stack View:**

>
- _Spacing_: Change from `0` to `35`
>

**Bill Amount Title Label (Inner Top Stack View):**

- _Text_: Change from `Label` to `Bill Amount`
- _Font_: Change from `System 17.0` to `System 20.0`
- _Color_: Change from `Default` to `tcWhite`
- _Alignment_: Change from `---` to `Left Aligned`

**Bill Amount Text Field (Inner Top Stack View):**

- _Alignment_: Change from `---` to `Center Aligned`
- _Placeholder_: Change from empty to `$0.00`
- _Correction_: Change from `Default` to `No`
- _Keyboard Type_: Change from `Default` to `Decimal Pad`
- _Keyboard Look_: Change from `Default` to `Light`
- _Tint_: Change from `Default` to `tcHotPink`

**Tip Percent Title Label (Inner Bottom Stack View):**

- _Text_: Change from `Label` to `Tip %`
- _Font_: Change from `System 17.0` to `System 20.0`
- _Color_: Change from `Default` to `tcWhite`
- _Alignment_: Change from `---` to `Left Aligned`

**Tip Percent Segmented Control (Inner Bottom Stack View):**

- _Segments_: Change from `2` to `3`
- _Tint_: Change from `Default` to `tcHotPink`

The last attribute we'll need to set is the title for each segment our segmented control.

> [action] For each segment of your segmented control, set the title attribute to `15%`, `18%`, `20%` respectively:
>

![ms-video](assets/set_segmented_control_titles.gif)

Time to build build and run your project to see your progress.

![Input Card Styled](assets/input_card_styled.png)

Bam! Your app matches the design (with exception of the rounded corners of course).

> [info] Rounded corners (and shadows) make use of our view's layer property. We'll cover this later in this tutorial.

Let's continue by creating the IB connections needed for our input card.

## Adding Our IB Connections

You've done this before with the header view. Get some more practice creating IB connections.

Create an `IBOutlet` for our input card (`UIView`).

> [action] Create an `IBOutlet ` for the input card view:
>
> Step-by-step:
>
> 1. Open `Main.storyboard` in your _Editor area_.
> 2. Option-click on `ViewController.swift` in your _Project Navigator_ to open it in your _Assitant Editor_.
> 3. (Optional) Hide the _Utilities area_ to make more screen space for the _Assistant Editor_.
> 4. Select the input card view (`UIView`).
> 5. With your input card selected, hold down control and click-drag from the input card to your `ViewController` class.
> 6. In the popup, set the _Name_ field to `inputCardView` and click connect to create your new outlet.

![ms-video](assets/input_card_ib_connections.png)

<!-- break -->

> [challenge] Now it's your turn to practice. If you find yourself stuck, look back on how we implemented our previous `IBOutlets` to refresh your memory.
>
Create the following `IBOutlets`:
>
- `UITextField` named `billAmountTextField`
- `UISegmentedControl` named `tipPercentSegmentedControl`

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

![textfield and segemented iboutlets](assets/textfield_and_segemented_iboutlet.gif)

Finally, we'll need to create an `IBAction` for our segmented control.

> [challenge] Try implementing an `IBAction` for your `UISegmentedControl`. Set the _Name_ as `tipPercentChanged` and check that the _Event type_ is `Value Changed`. If you get stuck, you can look back in the tutorial or check the solution (only if you're really stuck!)

-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-
-

<!-- break -->

> [solution] Creating an `IBAction` is similar to creating an `IBOutlet`:
>
> Step-by-step:
>
> 1. Select your segmented control (`UISegmentedControl`) in the _Document Outline_.
> 2. With your segmented control selected, hold down ctrl and click-drag from the segmented control in your _Document Outline_ to your `ViewController` class.
> 3. You should see a popup for creating a new IB connection. In the popup, change the _Connection_ type from `Outlet` to `Action`.
> 4. Set the name of our action as `tipPercentChanged`.
> 5. Change the _Type_ property from `Any` to `UISegmentedControl`.
> 6. Make sure the _Event_ property is set as `Value Changed`. If not, use the dropdown to set it to `Value Changed`.
> 7. Click _Connect_ to create your new `IBAction`.

![ms-video](assets/segmented_control_ibaction.gif)

When you're done, your storyboard and Swift code should look like the following:

![Input Card IB Connections](assets/input_card_ib_connections.png)

<!-- TODO: add custom textfield, but don't do that here -->

# Continue to the next section

[Tip Calculator Logic](../P05-Output-Card/)