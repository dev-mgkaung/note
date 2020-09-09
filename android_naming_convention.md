
# Naming Convention for Android Development

## Package Structure

> See this [Package by feature, not layer][1] 

<!--
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>` - contain Application class **only**
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.activity` - contain all activities
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.adapter` - contain all adapters
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.api` - contain all network related classes
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.fragment` - contain all fragments 
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.model` - contain all models 
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.provider` - contain all database related classes
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.receiver` - contain all broadcast receiver classes
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.service` - contain all services 
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.util` - contain all utility classes
 - `com.<COMPANY_NAME>.<PRODUCT_NAME>.widget`- contain all custom views
-->

## Naming Convention for Classes

 - `<PRODUCT_NAME>Application.java` - for Application class
 - `<NAME>Activity.java` - for activity class
 - `<NAME>Adapter.java` - for adapter class
 - `<NAME>Fragment.java` - for fragment class
 - `<NAME>.java` - for model class
 - `<NAME>Provider.java` - for content provider class
 - `<NAME>Service.java` - for service class
 - `<NAME>Receiver.java` - for broadcast receiver class
 - `<NAME>Utils.java` - for utility class
 - `<NAME>.java` - for custom view class

## Short Name of Android Widgets

> **Note**: You should use more meaningful names than these short names unless you have two or more same kind of views in the same place.

 - `aclock` - AnalogClock
 - `actv` - AutoCompleteTextView
 - `btn` - Button
 - `cal` - CalendarView
 - `chb` - CheckBox
 - `chtv` - CheckedTextView
 - `chron` - Chronometer
 - `dp` - DatePicker
 - `edt` - EditText
 - `explv` - ExpandableListView
 - `fl` - FrameLayout
 - `gl` - GridLayout
 - `grv` - GridView
 - `hsv` - HorizontalScrollView
 - `imb` - ImageButton
 - `ims` - ImageSwitcher
 - `imv` - ImageView
 - `ll` - LinearLayout
 - `lsv` - ListView
 - `ctlr` - MediaController
 - `mactv` - MultiAutoCompleteTextView
 - `np` - NumberPicker
 - `pm` - PopupMenu
 - `pw` - PopupWindow
 - `pgb` - ProgressBar
 - `rb` - RadioButton
 - `rg` - RadioGroup
 - `rtb` - RatingBar
 - `rl` - RelativeLayout
 - `rv` - RemoteViews
 - `scv` - ScrollView
 - `schv` - SearchView
 - `skb` - SeekBar
 - `sap` - ShareActionProvider
 - `space` - Space
 - `spn` - Spinner
 - `stv` - StackView
 - `sw` - Switch
 - `tabh` - TabHost
 - `tabc` - TabHost.TabSpec
 - `tl` - TableLayout
 - `tr` - TableRow
 - `twg` - TabWidget
 - `tclock` - TextClock
 - `tsw` - TextSwitcher
 - `txv` - TextView
 - `tp` - TimePicker
 - `toast` - Toast
 - `tgb` - ToggleButton
 - `vdv` - VideoView
 - `vf` - ViewFlipper
 - `vsw` - ViewSwitcher

## Naming Convention for Image Files
> See this [Android-Cheatsheet-For-Graphic-Designers#Naming Convention][2]
 
## XML Files (res/anim)

 - `<INTERPOLATOR_NAME>_interpolator.xml` - for custom interpolator
 - `<ANIMATION_NAME>.xml` - for custom animation

## XML Files (res/animator)

 - `<ANIMATOR_NAME>.xml`- for custom animator

## XML Files (res/color)

 - `selector_<COLOR_NAME>.xml` - for color state list

## XML Files (res/drawable)

 - `bmp_<BITMAP_NAME>.xml` - for bitmap file
 - `np_<NINE_PATCH_NAME>.xml` - for nine-patch XML file
 - `layer_<LAYER_LIST_NAME>.xml` - for layer list
 - `selector_<STATE_LIST_NAME>.xml` - for state list
 - `anim_<DRAWABLE_ANIMATION_NAME>.xml` - for drawable animation
 - `level_<LEVEL_LIST_NAME>.xml` - for level list
 - `trans_<TRANSITION_DRAWABLE_NAME>.xml` - for transition drawable
 - `inset_<INSET_DRAWABLE_NAME>.xml` - for inset drawable
 - `clip_<CLIP_DRAWABLE_NAME>.xml` - for clip drawable
 - `scale_<SCALE_DRAWABLE_NAME>.xml` - for scale drawable
 - `shape_<SHAPE_DRAWABLE_NAME>.xml` - for shape drawable

## XML Files (res/layout)

 - `activity_<ACTIVITY_NAME>.xml` - for activity
 - `dialog_<DIALOG_NAME>.xml` - for dialog
 - `list_item_<LIST_NAME>.xml` - for list item in ListView
 - `grid_item_<GRID_NAME>.xml` - for grid item in GridView
 - `fragment_<FRAGMENT_NAME>.xml` - for fragment
 - `layout_<LAYOUT_NAME>.xml` - for re-useable layout
 - `merge_<MERGE_NAME>.xml` - for `<merge>` Tag **only**
 - `widget_<WIDGET_NAME>.xml` - for custom view
 - `appwidget_<APPWIDGET_NAME>.xml` - for app widget

## XML Files (res/menu)

 - `<MENU_NAME>.xml` - for option menu
 - `contextual_<MENU_NAME>.xml` - for contextual menu
 - `popup_<MENU_NAME>.xml` - for popup menu

## XML Files (res/values)

 - values/colors.xml
 
    - `<color name="<THEME_NAME>_<COLOR_NAME>"><COLOR_VALUE></color>`
    
        For example: 
        ```
        <color name=”holo_blue_dark”>#ff0099cc</color> 
        <color name=”material_blue_500”>#5677fc</color>
        ```

    - If the color is not in the theme: 
      
      `<color name="<COLOR_NAME>"><COLOR_VALUE></color>`

 - values/strings.xml
    - `<string name="title_<TITLE_NAME>"><TITLE_VALUE></string>` - for ActionBar title
    - `<string name="action_<ACTION_BUTTON_TEXT>"><TEXT_VALUE></string>` - for ActionBar button text
    - `<string name="tab_<ACTION_TAB_TEXT>"><TEXT_VALUE></string>` - for ActionBar.Tab text
    - `<string name="btn_<BUTTON_TEXT>"><TEXT_VALUE></string>`- for button
    - `<string name="empty_<VIEW_NAME>"><EMPTY_VALUE></string>` - for empty view
    - `<string name="hint_<EDITTEXT_NAME>"><HINT_VALUE></string>`- for the hint of EditText/AutoCompleteTextView
    - `<string name="label_<TEXTVIEW_NAME>"><TEXT_VALUE></string>`- for static TextView
    - `<string name="toast_<TOAST_NAME>"><TOAST_VALUE></string>` - for toast
    - `<string name="dialog_title_<DIALOG_NAME>"><TITLE_VALUE></string>`- for dialog
    - `<string name="dialog_msg_<DIALOG_NAME>"><MSG_VALUE></string>` - for dialog
    - `<string name="dialog_action_<ACTION_NAME>"><ACTION_NAME></string>` - for dialog button
    - `<string name="msg_<MESSAGE_NAME>"><MSG_VALUE></string>` - for Log or some other stuff
    - `<string name="contextual_<MENU_ITEM_NAME>"><TEXT_VALUE></string>`- for contextual menu item
    - `<string name="popup_<MENU_ITEM_NAME>"><TEXT_VALUE></string>` - for popup menu item
    
 - values/string_arrays.xml

    `<string-array name="<ARRAY_NAME>_array">`

 - values/plurals.xml

    `<plurals name="<PLURALS_NAME>">`
    
<!-- values/attrs.xml values/dimens.xml values/styles.xml values/themes.xml values/ids.xml values/bools.xml -->

## XML Files (res/xml)

 - `appwidget_<APPWIDGET_NAME>` - for app widget provider

  [1]:http://www.javapractices.com/topic/TopicAction.do;jsessionid=0BF4844350780B6F55476E1137FF4893?Id=205
  [2]:http://petrnohejl.github.io/Android-Cheatsheet-For-Graphic-Designers/#naming-conventions
  
  ## Fields definition and naming
Fields should be defined at the top of the file and they should follow the naming rules listed below.

- Private, non-static field names start with m.
- Private, static field names start with s.
- Other fields start with a lower case letter.
- Static final fields (constants) are ALL_CAPS_WITH_UNDERSCORES.
- For components in addition to the top rules,we use component+description. 
### Example:

```
public class MyClass {
    public static final int SOME_CONSTANT = 42;
    public int publicField;
    private static MyClass sSingleton;
    int mPackagePrivate;
    private int mPrivate;
    protected int mProtected;
    private String mTitle;
    private TextView mTextViewTitle;
    private LinearLayout mLinearLayoutPhone;
    private Button mButtonSignIn;
}
```

## Use standard brace style

Braces do not go on their own line; they go on the same line as the code before them:

```
class MyClass {
    int func() {
        if (something) {
            // ...
        } else if (somethingElse) {
            // ...
        } else {
            // ...
        }
    }
}

```
We require braces around the statements for a conditional. Exception: If the entire conditional (the condition and the body) fit on one line, you may (but are not obligated to) put it all on one line. For example, this is acceptable:

```
if (condition) {
    body();
}

```
and this is acceptable:

`if (condition) body();`

but this is not acceptable:

```
if (condition)
    body();  // bad!
```
## Treat acronyms as words

Treat acronyms and abbreviations as words in naming variables, methods, and classes to make names more readable:

Good | Bad
-- | --
XmlHttpRequest | XMLHTTPRequest
getCustomerId | getCustomerID
class Html | class HTML
String url | String URL
long id | long ID

## Use TODO comments

Use TODO comments for code that is temporary, a short-term solution, or good-enough but not perfect. TODOs should include the string TODO in all caps, followed by a colon:

> // TODO: Remove this code after the UrlTable2 has been checked in.

and

> // TODO: Change this to use a flag instead of a constant.

If your TODO is of the form "At a future date do something" make sure that you either include a very specific date ("Fix by November 2005") or a very specific event ("Remove this code after all production mixers understand protocol V7.").

## Javatests style rules

Follow test method naming conventions and use an underscore to separate what is being tested from the specific case being tested. This style makes it easier to see exactly what cases are being tested. For example:

```
testMethod_specificCase1 testMethod_specificCase2

void testIsDistinguishable_protanopia() {
    ColorMatcher colorMatcher = new ColorMatcher(PROTANOPIA)
    assertFalse(colorMatcher.isDistinguishable(Color.RED, Color.BLACK))
    assertTrue(colorMatcher.isDistinguishable(Color.X, Color.Y))
}

```

## Database name convention
Singular names for tables.
Singular names for columns.
Schema name for tables prefix (E.g.: SchemeName.TableName).
Pascal casing (a.k.a. upper camel case). Example: FlightNumber

 ## Logging guidelines
Use the logging methods provided by the `Log` class to print out error messages or other information that may be useful for developers to identify issues:
- `Log.v(String tag, String msg)` (verbose)
- `Log.d(String tag, String msg)` (debug)
- `Log.i(String tag, String msg)` (information)
- `Log.w(String tag, String msg) `(warning)
- `Log.e(String tag, String msg)` (error)

As a general rule, we use the class name as tag and we define it as a `static final` field at the top of the file. For example:

```
public class MyClass {
    private static final String TAG = MyClass.class.getSimpleName();

    public myMethod() {
        Log.e(TAG, "My error message");
    }
}
```

VERBOSE and DEBUG logs must be disabled on release builds. It is also recommended to disable INFORMATION, WARNING and ERROR logs but you may want to keep them enabled if you think they may be useful to identify issues on release builds. If you decide to leave them enabled, you have to make sure that they are not leaking private information such as email addresses, user ids, etc.

To only show logs on debug builds:
`if (BuildConfig.DEBUG) Log.d(TAG, "The value of x is " + x);`

## Resources
![resourcenaming_cheatsheet](https://user-images.githubusercontent.com/31917346/40650319-4206bddc-6348-11e8-9e7c-8c61e7d03c27.png)

### Layouts

Layouts are relatively simple, as there usually are only a few layouts per screen. Therefore the rule can be simplified to:
![layouts](https://user-images.githubusercontent.com/31917346/40650666-1301d520-6349-11e8-8e03-884c74159bf4.png)

Prefix | Usage
-- | --
activity | contentview for activity
fragment | view for a fragment
view | inflated by a custom view
item | layout used in list/recycler/gridview
layout | layout reused using the include tag
### Examples:

- activity_main: content view of the MainActivity
- fragment_articledetail: view for the ArticleDetailFragment
- view_menu: layout inflated by custom view class MenuView
- item_article: list item in ArticleRecyclerView
- layout_actionbar_backbutton: layout for an actionbar with a backbutton (too simple to be a customview)

### Strings

The `<WHAT>` part for Strings is irrelevant. So either we use `<WHERE>` to indicate where the string will be used:
![strings](https://user-images.githubusercontent.com/31917346/40650948-c6fe0cba-6349-11e8-9333-404f0b510724.png)
or `all` if the string is reused throughout the app:
![strings2](https://user-images.githubusercontent.com/31917346/40650998-e07f01c6-6349-11e8-8cb8-03df9a3fbf64.png)
### Examples:

- articledetail_title: title of ArticleDetailFragment
- feedback_explanation: feedback explanation in FeedbackFragment
- feedback_namehint: hint of name field in FeedbackFragment
- all_done: generic “done” string


`<WHERE> `obviously is the same for all resources in the same view.

### Drawables

The `<WHAT>` part for Drawables is irrelevant. So either we use `<WHERE>` to indicate where the drawable will be used:
![drawables](https://user-images.githubusercontent.com/31917346/40651174-4c8b9b72-634a-11e8-951c-e9a67add1b07.png)
or `all` if the drawable is reused throughout the app:
![drawables2](https://user-images.githubusercontent.com/31917346/40651253-79d276c8-634a-11e8-92a1-f1c646636970.png)
Optionally you can add a `<SIZE>` argument, which can be an actual size “24dp” or a size qualifier “small”.
### Examples:

 

- articledetail_placeholder: placeholder in ArticleDetailFragment
- all_infoicon: generic info icon
- all_infoicon_large: large version of generic info icon
- all_infoicon_24dp: 24dp version of generic info icon

### IDs

For IDs, `<WHAT>` is the class name of the xml element it belongs to. Next is the screen the ID is in, followed by an optional description to distinguish similar elements in one screen.
![ids](https://user-images.githubusercontent.com/31917346/40651432-eee2227e-634a-11e8-9e5b-dc3c4a998fd2.png)
### Examples:

- tablayout_main -> TabLayout in MainActivity
- imageview_menu_profile -> profile image in custom MenuView
- textview_articledetail_title -> title TextView in ArticleDetailFragment

### Dimensions

Apps should only define a limited set of dimensions, which are constantly reused. This makes most dimensions `all` by default.
Therefore you should mostly use:
![dimensions2](https://user-images.githubusercontent.com/31917346/40651823-df7f1908-634b-11e8-80b3-f78e28b9aee8.png)
and optionally use the screen specific variant:
![dimensions](https://user-images.githubusercontent.com/31917346/40651661-83d71754-634b-11e8-88ca-8da5543fe832.png)
Where `<WHAT>` is one of the following:

Prefix | Usage
-- | --
width | width in dp
height | height in dp
size | if width == height
margin | margin in dp
padding | padding in dp
elevation | elevation in dp
keyline | absolute keyline measured from view edge in dp
textsize | size of text in sp

Note that this list only contains the most used `<WHAT>`s. Other dimensions qualifiers like: rotation, scale,… are usually only used in drawables and as such less reused.
### Examples:

- height_toolbar: height of all toolbars
- keyline_listtext: listitem text is aligned at this keyline
- textsize_medium: medium size of all text
- size_menu_icon: size of icons in menu
- height_menu_profileimage: height of profile image in menu


reference :[https://jeroenmols.com/blog/2016/03/07/resourcenaming/]( https://jeroenmols.com/blog/2016/03/07/resourcenaming/)
