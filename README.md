Adopting Liquid Glass
Find out how to bring the new material to your app.
Overview
If you have an existing app, adopting Liquid Glass doesn’t mean reinventing your app from the ground up. Start by building your app in the latest version of Xcode to see the changes. As you review your app, use the following sections to understand the scope of changes and learn how you can adopt these best practices in your interface.

An image of a Mac, iPad, and iPhone showing the Mount Fuji landmark in the Landmarks app.

See your app with Liquid Glass
If your app uses standard components from SwiftUI, UIKit, or AppKit, your interface picks up the latest look and feel on the latest platform releases for iOS, iPadOS, macOS, tvOS, and watchOS. In Xcode, build your app with the latest SDKs, and run it on the latest platform releases to see the changes in your interface.

Visual refresh
Interfaces across Apple platforms feature a new dynamic material called Liquid Glass, which combines the optical properties of glass with a sense of fluidity. This material forms a distinct functional layer for controls and navigation elements. It affects how the interface looks, feels, and moves, adapting in response to a variety of factors to help bring focus to the underlying content.

Leverage system frameworks to adopt Liquid Glass automatically. In system frameworks, standard components like bars, sheets, popovers, and controls automatically adopt this material. System frameworks also dynamically adapt these components in response to factors like element overlap and focus state. Take advantage of this material with minimal code by using standard components from SwiftUI, UIKit, and AppKit.

Reduce your use of custom backgrounds in controls and navigation elements. Any custom backgrounds and appearances you use in these elements might overlay or interfere with Liquid Glass or other effects that the system provides, such as the scroll edge effect. Make sure to check any custom backgrounds in elements like split views, tab bars, and toolbars. Prefer to remove custom effects and let the system determine the background appearance, especially for the following elements:

SwiftUI
UIKit
AppKit
NavigationStack

NavigationSplitView

titleBar

toolbar(content:)

Test your interface with accessibility settings. Translucency and fluid morphing animations contribute to the look and feel of Liquid Glass, but can adapt to people’s needs. For example, people might turn on accessibility settings that reduce transparency or motion in the interface, which can remove or modify certain effects. If you use standard components from system frameworks, this experience adapts automatically. Ensure your custom elements and animations provide a good fallback experience when these settings are on as well.

Avoid overusing Liquid Glass effects. If you apply Liquid Glass effects to a custom control, do so sparingly. Liquid Glass seeks to bring attention to the underlying content, and overusing this material in multiple custom controls can provide a subpar user experience by distracting from that content. Limit these effects to the most important functional elements in your app. To learn more, read Applying Liquid Glass to custom views.

SwiftUI
UIKit
AppKit
glassEffect(_:in:)

App icons
App icons take on a design that’s dynamic and expressive. Updates to the icon grid result in a standardized iconography that’s visually consistent across devices and concentric with hardware and other elements across the system. App icons now contain layers, which dynamically respond to lighting and other visual effects the system provides. iOS, iPadOS, and macOS all now offer default (light), dark, clear, and tinted appearance variants, empowering people to personalize the look and feel of their Home Screen.

A grid showing the Podcasts app icon in the six style variants: default, dark, clear (light), clear (dark), tinted (light), and tinted (dark).

Reimagine your app icon for Liquid Glass. Apply key design principles to help your app icon shine:

Provide a visually consistent, optically balanced design across the platforms your app supports.

Consider a simplified design comprised of solid, filled, overlapping semi-transparent shapes.

Let the system handle applying masking, blurring, and other visual effects, rather than factoring them into your design.

The Podcasts app icon in iOS 18 using the light style.
Podcasts icon in iOS 18

The Podcasts app icon in iOS using the default style, shown before applying system effects. The design of the icon uses solid filled shapes instead of outlines, and multiple layers of varying opacity.
Reimagined layered Podcasts icon

The Podcasts app icon in iOS using the default style, shown with system effects applied.
Reimagined layered Podcasts icon with system effects applied

Design using layers. The system automatically applies effects like reflection, refraction, shadow, blur, and highlights to your icon layers. Determine which elements of your design make sense as foreground, middle, and background elements, then define separate layers for them. You can perform this task in the design app of your choice.

Compose and preview in Icon Composer. Drag and drop app icon layers that you export from your design app directly into the Icon Composer app. Icon Composer lets you add a background, create layer groupings, adjust layer attributes like opacity, and preview your design with system effects and appearances. Icon Composer is available in the latest version of Xcode and for download from Apple Design Resources. To learn more, read Creating your app icon using Icon Composer.

A screenshot of the Icon Composer app showing the Podcasts app icon in the default style.

Preview against the updated grids. The system applies masking to produce your final icon shape — rounded rectangle for iOS, iPadOS, and macOS, and circular for watchOS. Keep elements centered to avoid clipping. Irregularly shaped icons receive a system-provided background. See how your app icon looks with the updated grids to determine whether you need to make adjustments. Download these grids from Apple Design Resources.

Controls
Controls have a refreshed look across platforms, and come to life when a person interacts with them. For controls like sliders and toggles, the knob transforms into Liquid Glass during interaction, and buttons fluidly morph into menus and popovers. The shape of the hardware informs the curvature of controls, so many controls adopt rounder forms to elegantly nestle into the corners of windows and displays. Controls also feature an option for an extra-large size, allowing more space for labels and accents.

Play
Slider
Play
Segmented control
Review updates to control appearance and dimensions. If you use standard controls from system frameworks, your app adopts changes to shapes and sizes automatically when you rebuild your app with the latest version of Xcode. Review changes to the following controls and any others and make sure they continue to look at home with the rest of your interface:

SwiftUI
UIKit
AppKit
Button

Toggle

Slider

Stepper

Picker

TextField

Review your use of color in controls. Be judicious with your use of color in controls and navigation so they stay legible and keep the focus on your content. If you do apply color to these elements, leverage system colors to automatically adapt to light and dark contexts.

Check for crowding or overlapping of controls. Allow Liquid Glass room to move and breathe, and avoid overcrowding or layering elements on top of each other.

Navigation
Liquid Glass applies to the topmost layer of the interface, where you define your navigation. Key navigation elements like tab bars and sidebars float in this Liquid Glass layer to help people focus on the underlying content.

A screenshot of the bottom half of an iPhone showing a tab bar as it appears in iOS 18 and earlier.
Before

A screenshot of the bottom half of an iPhone showing a tab bar as it appears in the latest version of iOS. The search tab appears in its own section at the trailing end of the tab bar.
After

Establish a clear navigation hierarchy. It’s more important than ever for your app to have a clear and consistent navigation structure that’s distinct from the content you provide. Ensure that you clearly separate your content from navigation elements, like tab bars and sidebars, to establish a distinct functional layer above the content layer.

Consider adapting your tab bar into a sidebar automatically. If your app uses a tab-based navigation, you can allow the tab bar to adapt into a sidebar depending on the context by using the following APIs:

SwiftUI
UIKit
sidebarAdaptable

Consider using split views to build sidebar layouts with an inspector panel. Split views are optimized to create a consistent and familiar experience for sidebar and inspector layouts across platforms. You can use the following standard system APIs for split views to build these types of layouts with minimal code:

SwiftUI
UIKit
AppKit
NavigationSplitView

inspector(isPresented:content:)

Check content safe areas for sidebars and inspectors. If you have these types of components in your app’s navigation structure, audit the safe area compatibility of content next to the sidebar and inspector to help make sure underlying content is peeking through appropriately.

Extend content beneath sidebars and inspectors. A background extension effect creates a sense of extending a background under a sidebar or inspector, without actually scrolling or placing content under it. A background extension effect mirrors the adjacent content to give the impression of stretching it under the sidebar, and applies a blur to maintain legibility of the sidebar or inspector. This effect is perfect for creating a full, edge-to-edge content experience in apps that use split views, such as for hero images on product pages.

A screenshot of the Landmarks app showing the sidebar. The image next to the sidebar doesn't extend beneath it, so the sidebar floats above an empty background.
Without background extension effect

A screenshot of the Landmarks app showing the sidebar. The image next to the sidebar gives the impression of extending beneath it using the background extension effect.
With background extension effect

SwiftUI
UIKit
AppKit
backgroundExtensionEffect()

Choose whether to automatically minimize your tab bar in iOS. Tab bars can help elevate the underlying content by receding when a person scrolls up or down. You can opt into this behavior and configure the tab bar to minimize when a person scrolls down or up. The tab bar expands when a person scrolls in the opposite direction.

SwiftUI
UIKit
TabView {
    // ...
}
.tabBarMinimizeBehavior(.onScrollDown)
Menus and toolbars
Menus have a refreshed look across platforms. They adopt Liquid Glass, and menu items for common actions use icons to help people quickly scan and identify those actions. New to iPadOS, apps also have a menu bar for faster access to common commands.

Adopt standard icons in menu items. For menu items that perform standard actions like Cut, Copy, and Paste, the system uses the menu item’s selector to determine which icon to apply. To adopt icons in those menu items with minimal code, make sure to use standard selectors.

Match top menu actions to swipe actions. For consistency and predictability, make sure the actions you surface at the top of your contextual menu match the swipe actions you provide for the same item.

Toolbars take on a Liquid Glass appearance, and provide a grouping mechanism for toolbar items, letting you choose which actions to display together.

A screenshot of the bottom half of an iPhone showing a toolbar as it appears in iOS 18 and earlier.
Before

A screenshot of the bottom half of an iPhone showing a toolbar as it appears in the latest version of iOS.
After

Determine which toolbar items to group together. Group items that perform similar actions or affect the same part of the interface, and maintain consistent groupings and placement across platforms.

A graphic that shows a toolbar with four buttons that all share a background: Undo, Redo, Markup, and More.
Incorrect

A graphic that shows a toolbar with the four buttons split into two groupings according to their functions. The Undo and Redo buttons share a background, and the Markup and More buttons share a background.
Correct

You can create a fixed spacer to separate items that share a background using these APIs:

SwiftUI
UIKit
AppKit
fixed

ToolbarSpacer

Find icons to represent common actions. Consider representing common actions in toolbars with standard icons instead of text. This approach helps declutter the interface and increase the ease of use for common actions. For consistency, don’t mix text and icons across items that share a background.

Provide an accessibility label for every icon. Regardless of what you show in the interface, always specify an accessibility label for each icon. This way, people who prefer a text label can opt into this information by turning on accessibility features like VoiceOver or Voice Control.

Audit toolbar customizations. Review anything custom you do to display items in your toolbars, like your use of fixed spacers or custom items, as these can appear inconsistent with system behavior.

Check how you hide toolbar items. If you see an empty toolbar item without any content, your app might be hiding the view in the toolbar item instead of the item itself. Instead, hide the entire toolbar item, using these APIs:

SwiftUI
UIKit
AppKit
hidden(_:)

Windows and modals
Windows adopt rounder corners to fit controls and navigation elements. In iPadOS, apps show window controls and support continuous window resizing. Instead of transitioning between specific preset sizes, windows resize fluidly down to a minimum size.

Support arbitrary window sizes. Allow people to resize their window to the width and height that works for them, and adjust your content accordingly.

Use split views to allow fluid resizing of columns. To support continuous window resizing, split views automatically reflow content for every size using beautiful, fluid transitions. Make sure to use standard system APIs for split views to get these animations with minimal code:

SwiftUI
UIKit
AppKit
NavigationSplitView

Use layout guides and safe areas. Make sure you specify safe areas for your content so the system can automatically adjust the window controls and title bar in relation to your content.

Modal views like sheets and action sheets adopt Liquid Glass. Sheets feature an increased corner radius, and half sheets are inset from the edge of the display to allow content to peek through from beneath them. When a half sheet expands to full height, it transitions to a more opaque appearance to help maintain focus on the task.

Check the content around the edges of sheets. Inside the sheet, check for content and controls that might appear too close to rounder sheet corners. Outside the sheet, check that any content peeking through between the inset sheet and display edge looks as you expect.

Audit the backgrounds of sheets and popovers. Check whether you add a visual effect view to your popover’s content view, and remove those custom background views to provide a consistent experience with other sheets across the system.

An action sheet originates from the element that initiates the action, instead of from the bottom edge of the display. When active, an action sheet also lets people interact with other parts of the interface.

Specify the source of an action sheet. Position an action sheet’s anchor next to the control it originates from. Make sure to set the source view or item to indicate where to originate the action sheet and create the inline appearance.

SwiftUI
UIKit
AppKit
confirmationDialog(_:isPresented:titleVisibility:presenting:actions:)

Organization and layout
Style updates to list-based layouts help you organize and showcase your content so it can shine through the Liquid Glass layer. To give content room to breathe, organizational components like lists, tables, and forms have a larger row height and padding. Sections have an increased corner radius to match the curvature of controls across the system.

A screenshot of an iPhone showing a grouped list layout as it appears in iOS 18 and earlier.
Before

A screenshot of an iPhone showing a grouped list layout as it appears in the latest version of iOS.
After

Check capitalization in section headers. Lists, tables, and forms optimize for legibility by adopting title-style capitalization for section headers. This means section headers no longer render entirely in capital letters regardless of the capitalization you provide. Make sure to update your section headers to title-style capitalization to match your app’s text to this systemwide convention.

Adopt forms to take advantage of layout metrics across platform. Use SwiftUI forms with the grouped form style to automatically update your form layouts.

Search
Platform conventions for location and behavior of search optimize the experience for each device and use case. To provide an engaging search experience in your app, review these search design conventions.

A graphic of an iPad showing search in a toolbar in the upper trailing corner.
Search in a toolbar on iPad

A graphic of an iPhone showing search in a toolbar at the bottom of the screen.
Search in a toolbar on iPhone

Check the keyboard layout when activating your search interface. In iOS, when a person taps a search field to give it focus, it slides upwards as the keyboard appears. Test this experience in your app to make sure the search field moves consistently with other apps and system experiences.

Use semantic search tabs. If your app’s search appears as part of a tab bar, make sure to use the standard system APIs for indicating which tab is the search tab. The system automatically separates the search tab from other tabs and places it at the trailing end to make your search experience consistent with other apps and help people find content faster.

SwiftUI
UIKit
Tab(role: .search) {
    // ...
}
Platform considerations
Liquid Glass can have a distinct appearance and behavior across different platforms, contexts, and input methods. Test your app across devices to understand how the material looks and feels across platforms.

In watchOS, adopt standard button styles and toolbar APIs. Liquid Glass changes are minimal in watchOS, so they appear automatically when you open your app on the latest release even if you don’t build against the latest SDK. However, to make sure your app picks up this appearance, adopt standard toolbar APIs and button styles from watchOS 10.

Combine custom Liquid Glass effects to improve rendering performance. If you apply these effects to custom elements, make sure to combine them using a GlassEffectContainer, which helps optimize performance while fluidly morphing Liquid Glass shapes into each other.

Performance test your app across platforms. It’s a good idea to regularly assess and improve your app’s performance, and building your app with the latest SDKs provides an opportunity to check in. Profile your app to gather information about its current performance and find any opportunities for improving the user experience. To learn more, read Improving your app’s performance.

To update and ship your app with the latest SDKs while keeping your app as it looks when built against previous versions of the SDKs, you can add the UIDesignRequiresCompatibility key to your information property list.


Applying Liquid Glass to custom views
Configure, combine, and morph views using Liquid Glass effects.
Overview
Interfaces across Apple platforms feature a new dynamic material called Liquid Glass, which combines the optical properties of glass with a sense of fluidity. Liquid Glass is a material that blurs content behind it, reflects color and light of surrounding content, and reacts to touch and pointer interactions in real time. Standard components in SwiftUI use Liquid Glass. Adopt Liquid Glass on custom components to move, combine, and morph them into one another with unique animations and transitions.

An image of the Landmarks sample code on iPad, in landscape, showing the Mount Fuji landmark.

To learn about Liquid Glass and more, see Landmarks: Building an app with Liquid Glass.

Apply and configure Liquid Glass effects
Use the glassEffect(_:in:) modifier to add Liquid Glass effects to a view. By default, the modifier uses the regular variant of Glass and applies the given effect within a Capsule shape behind the view’s content.

Configure the effect to customize your components in a variety of ways:

Use different shapes to have a consistent look and feel across custom components in your app. For example, use a rounded rectangle if you’re applying the effect to larger components that would look odd as a Capsule or Circle.

Define a tint color to suggest prominence.

Add interactive(_:) to custom components to make them react to touch and pointer interactions. This applies the same responsive and fluid reactions that glass provides to standard buttons.

In the examples below, observe how to apply Liquid Glass effects to a view, use an alternate shape with a specific corner radius, and create a tinted view that responds to interactivity:

Play
Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect()


Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect(in: .rect(cornerRadius: 16.0))


Text("Hello, World!")
    .font(.title)
    .padding()
    .glassEffect(.regular.tint(.orange).interactive())
Combine multiple views with Liquid Glass containers
Use GlassEffectContainer when applying Liquid Glass effects on multiple views to achieve the best rendering performance. A container also allows views with Liquid Glass effects to blend their shapes together and to morph in and out of each other during transitions. Inside a container, each view with the glassEffect(_:in:) modifier renders with the effects behind it.

Customize the spacing on the container to set layout spacing between views and to affect how the Liquid Glass effects behind views interact with one another. Views close to one another merge their effects into a single shape. The farther views are from each other, the sooner the shapes merge into each other.

The .glassEffect() modifier captures the content to send to the container to render. Apply the .glassEffect() modifier after other modifiers that will affect the appearance of the view.

In the example below, two images are placed close to each other and the Liquid Glass effects begin to blend their shapes together. This creates a fluid animation as components move around each other within a container:

Two Image views representing a scribble symbol on the left, and an eraser symbol on the right. The views are close to each other, which causes the Liquid Glass effects to merge the views.

GlassEffectContainer(spacing: 40.0) {
    HStack(spacing: 40.0) {
        Image(systemName: "scribble.variable")
            .frame(width: 80.0, height: 80.0)
            .font(.system(size: 36))
            .glassEffect()


        Image(systemName: "eraser.fill")
            .frame(width: 80.0, height: 80.0)
            .font(.system(size: 36))
            .glassEffect()


            // An `offset` shows how Liquid Glass effects react to each other in a container.
            // Use animations and components appearing and disappearing to obtain effects that look purposeful.
            .offset(x: -40.0, y: 0.0)
    }
}
In some cases, you want the geometries of multiple views to contribute to a single Liquid Glass effect capsule, even when your content is at rest. Use the glassEffectUnion(id:namespace:) modifier to specify that a view contributes to a united effect with a particular ID. This combines all effects with a similar shape, Liquid Glass effect, and ID into a single shape with the applied Liquid Glass material. This is especially useful when creating views dynamically, or with views that live outside of an HStack or VStack.

Four Image views that have Liquid Glass effects applied. A rain cloud with lightning symbol and a sun with rain symbol have a unioned Liquid Glass effect encapsulating both of them, followed by a unioned Liquid Glass effect of a moon with stars symbol and a moon symbol.

let symbolSet: [String] = ["cloud.bolt.rain.fill", "sun.rain.fill", "moon.stars.fill", "moon.fill"]


GlassEffectContainer(spacing: 20.0) {
    HStack(spacing: 20.0) {
        ForEach(symbolSet.indices, id: \.self) { item in
            Image(systemName: symbolSet[item])
                .frame(width: 80.0, height: 80.0)
                .font(.system(size: 36))
                .glassEffect()
                .glassEffectUnion(id: item < 2 ? "1" : "2", namespace: namespace)
        }
    }
}
Morph Liquid Glass effects during transitions
Morphing effects occur during transitions between views with Liquid Glass effects. Add these transitions to views with effects in a container by using the glassEffectID(_:in:) modifier.

Associate each Liquid Glass effect with a unique identifier within a namespace the Namespace property wrapper provides. These IDs ensure SwiftUI animates the same shapes correctly when a shape appears or disappears due to view hierarchy changes. SwiftUI uses the spacing provided to the effect container along with the geometry of the shapes themselves to determine appropriate shapes to morph into and out of.

In the example below, the eraser image transitions into and out of the pencil image when the isExpanded variable changes. The GlassEffectContainer has a spacing value of 40.0, and the HStack within it has a spacing of 40.0. This morphs the eraser image into the pencil image when the eraser’s nearest edge is less than or equal to the container’s spacing.

Play
@State private var isExpanded: Bool = false
@Namespace private var namespace


var body: some View {
    GlassEffectContainer(spacing: 40.0) {
        HStack(spacing: 40.0) {
            Image(systemName: "scribble.variable")
                .frame(width: 80.0, height: 80.0)
                .font(.system(size: 36))
                .glassEffect()
                .glassEffectID("pencil", in: namespace)


            if isExpanded {
                Image(systemName: "eraser.fill")
                    .frame(width: 80.0, height: 80.0)
                    .font(.system(size: 36))
                    .glassEffect()
                    .glassEffectID("eraser", in: namespace)
            }
        }
    }


    Button("Toggle") {
        withAnimation {
            isExpanded.toggle()
        }
    }
    .buttonStyle(.glass)
}
See Also
Styling views with Liquid Glass
Landmarks: Building an app with Liquid Glass
Enhance your app experience with system-provided and custom Liquid Glass.
func glassEffect(Glass, in: some Shape) -> some View
Applies the Liquid Glass effect to a view.
Beta
func interactive(Bool) -> Glass
Returns a copy of the structure configured to be interactive.
Beta
struct GlassEffectContainer
A view that combines multiple Liquid Glass shapes into a single shape that can morph individual shapes into one another.
Beta
struct GlassEffectTransition
A structure that describes changes to apply when a glass effect is added or removed from the view hierarchy.
Beta
struct GlassButtonStyle
A button style that applies glass border artwork based on the button’s context.
Beta
struct GlassProminentButtonStyle
A button style that applies prominent glass border artwork based on the button’s context.
Beta
struct DefaultGlassEffectShape
The default shape applied by glass effects, a capsule.
Beta


SwiftUI
GlassButtonStyle
Beta
Structure
GlassButtonStyle
A button style that applies glass border artwork based on the button’s context.
iOS 26.0+
Beta
iPadOS 26.0+
Beta
Mac Catalyst 26.0+
Beta
macOS 26.0+
Beta
tvOS 26.0+
Beta
visionOS 26.0+
Beta
watchOS 26.0+
Beta
struct GlassButtonStyle
Overview
You can also use glass to construct this style.

Topics
Initializers
init()
Creates a glass button style.
Instance Methods
func makeBody(configuration: GlassButtonStyle.Configuration) -> some View
Creates a view that represents the body of a button.
Relationships
Conforms To
PrimitiveButtonStyle
See Also
Styling views with Liquid Glass
Applying Liquid Glass to custom views
Configure, combine, and morph views using Liquid Glass effects.
Landmarks: Building an app with Liquid Glass
Enhance your app experience with system-provided and custom Liquid Glass.
func glassEffect(Glass, in: some Shape) -> some View
Applies the Liquid Glass effect to a view.
Beta
func interactive(Bool) -> Glass
Returns a copy of the structure configured to be interactive.
Beta
struct GlassEffectContainer
A view that combines multiple Liquid Glass shapes into a single shape that can morph individual shapes into one another.
Beta
struct GlassEffectTransition
A structure that describes changes to apply when a glass effect is added or removed from the view hierarchy.
Beta
struct GlassProminentButtonStyle
A button style that applies prominent glass border artwork based on the button’s context.
Beta
struct DefaultGlassEffectShape
The default shape applied by glass effects, a capsule.
Beta


SwiftUI
GlassEffectTransition
Beta
Structure
GlassEffectTransition
A structure that describes changes to apply when a glass effect is added or removed from the view hierarchy.
iOS 26.0+
Beta
iPadOS 26.0+
Beta
Mac Catalyst 26.0+
Beta
macOS 26.0+
Beta
tvOS 26.0+
Beta
visionOS 26.0+
Beta
watchOS 26.0+
Beta
struct GlassEffectTransition
Topics
Type Properties
static var identity: GlassEffectTransition
The identity transition specifying no changes.
static var matchedGeometry: GlassEffectTransition
Returns the matched geometry glass effect transition.
static var materialize: GlassEffectTransition
The materialize glass effect transition which will fade in content and animate in or out the glass material but will not attempt to match the geometry of any other glass effects.
Relationships
Conforms To
Sendable
SendableMetatype
See Also
Styling views with Liquid Glass
Applying Liquid Glass to custom views
Configure, combine, and morph views using Liquid Glass effects.
Landmarks: Building an app with Liquid Glass
Enhance your app experience with system-provided and custom Liquid Glass.
func glassEffect(Glass, in: some Shape) -> some View
Applies the Liquid Glass effect to a view.
Beta
func interactive(Bool) -> Glass
Returns a copy of the structure configured to be interactive.
Beta
struct GlassEffectContainer
A view that combines multiple Liquid Glass shapes into a single shape that can morph individual shapes into one another.
Beta
struct GlassButtonStyle
A button style that applies glass border artwork based on the button’s context.
Beta
struct GlassProminentButtonStyle
A button style that applies prominent glass border artwork based on the button’s context.
Beta
struct DefaultGlassEffectShape
The default shape applied by glass effects, a capsule.
Beta
Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

Learn more about using Apple's beta software 


SwiftUI
GlassEffectContainer
Beta
Structure
GlassEffectContainer
A view that combines multiple Liquid Glass shapes into a single shape that can morph individual shapes into one another.
iOS 26.0+
Beta
iPadOS 26.0+
Beta
Mac Catalyst 26.0+
Beta
macOS 26.0+
Beta
tvOS 26.0+
Beta
watchOS 26.0+
Beta
@MainActor @preconcurrency
struct GlassEffectContainer<Content> where Content : View
Mentioned in
Applying Liquid Glass to custom views
Overview
Use a container with the glassEffect(_:in:) modifier. Each view with a Liquid Glass effect contributes a shape rendered with the effect to a set of shapes. SwiftUI renders the effects together, improving rendering performance and allowing the effects to interact with and morph into one another.

Configure how shapes interact with one another by customizing the default spacing value of the container. As shapes near one another, their paths start to blend into one another. The higher the spacing, the sooner blending begins as the shapes approach each other.

Topics
Initializers
init(spacing: CGFloat?, content: () -> Content)
Creates a glass effect container with the provided spacing, extracting glass shapes from the provided content.
Relationships
Conforms To
Sendable
SendableMetatype
View
See Also
Styling views with Liquid Glass
Applying Liquid Glass to custom views
Configure, combine, and morph views using Liquid Glass effects.
Landmarks: Building an app with Liquid Glass
Enhance your app experience with system-provided and custom Liquid Glass.
func glassEffect(Glass, in: some Shape) -> some View
Applies the Liquid Glass effect to a view.
Beta
func interactive(Bool) -> Glass
Returns a copy of the structure configured to be interactive.
Beta
struct GlassEffectTransition
A structure that describes changes to apply when a glass effect is added or removed from the view hierarchy.
Beta
struct GlassButtonStyle
A button style that applies glass border artwork based on the button’s context.
Beta
struct GlassProminentButtonStyle
A button style that applies prominent glass border artwork based on the button’s context.
Beta
struct DefaultGlassEffectShape
The default shape applied by glass effects, a capsule.
Beta
Beta Software

This documentation contains preliminary information about an API or technology in development. This information is subject to change, and software implemented according to this documentation should be tested with final operating system software.

Learn more about using Apple's beta software 


June 9, 2025

Added guidance for grouping bar items, updated guidance for using symbols, and incorporated navigation bar guidance.
Toolbars
A toolbar provides convenient access to frequently used commands, controls, navigation, and search.
A stylized representation of a toolbar, with a Back control on the leading edge, and Compose, Share, and the More menu on the trailing edge. The image is tinted red to subtly reflect the red in the original six-color Apple logo.

A toolbar consists of one or more sets of controls arranged horizontally along the top or bottom edge of the view, grouped into logical sections.

Toolbars act on content in the view, facilitate navigation, and help orient people in the app. They include three types of content:

The title of the current view

Navigation controls, like back and forward, and search fields

Actions, or bar items, like buttons and menus

In contrast to a toolbar, a tab bar is specifically for navigating between areas of an app.

Best practices
Choose items deliberately to avoid overcrowding. People need to be able to distinguish and activate each item, so you don’t want to put too many items in the toolbar. To accommodate variable view widths, define which items move to the overflow menu as the toolbar becomes narrower.

Note

The system automatically adds an overflow menu in macOS or iPadOS when items no longer fit. Don’t add an overflow menu manually, and avoid layouts that cause toolbar items to overflow by default.

Add a More menu to contain additional actions. Prioritize less important actions for inclusion in the More menu. Try to include all actions in the toolbar if possible, and only add this menu if you really need it.

Standard
Compact
A screenshot of the Notes app on Mac, with the window wide enough for the toolbar to include all of the available toolbar items. A More menu button appears on the trailing side of the toolbar, with the menu open beneath it.
The standard toolbar in macOS Notes includes a More menu with extra commands.

In iPadOS and macOS apps, consider letting people customize the toolbar to include their most common items. Toolbar customization is especially useful in apps that provide a lot of items — or that include advanced functionality that not everyone needs — and in apps that people tend to use for long periods of time. For example, it works well to make a range of editing actions available for toolbar customization, because people often use different types of editing commands based on their work style and their current project.

Reduce the use of toolbar backgrounds and tinted controls. Any custom backgrounds and appearances you use might overlay or interfere with background effects that the system provides. Instead, use the content layer to inform the color and appearance of the toolbar, and use a ScrollEdgeEffectStyle when necessary to distinguish the toolbar area from the content area. This approach helps your app express its unique personality without distracting from content.

Prefer using standard components in a toolbar. By default, standard buttons, text fields, headers, and footers have corner radii that are concentric with bar corners. If you need to create a custom component, ensure that its corner radius is also concentric with the bar’s corners.

Avoid using a segmented control in a toolbar. Segmented controls let people switch contexts, whereas a toolbar’s actions are specific to the current view. For guidance, see Segmented controls.

Consider temporarily hiding toolbars for a distraction-free experience. Sometimes people appreciate a minimal interface to reduce distractions or reveal more content. If you support this, do so contextually when it makes the most sense, and offer ways to reliably restore hidden interface elements. For guidance, see Going full screen. For guidance specific to visionOS, see Immersive experiences.

Titles
Provide a useful title for each window. A title helps people confirm their location as they navigate your app, and differentiates between the content of multiple open windows. If titling a toolbar seems redundant, you can leave the title area empty. For example, Notes doesn’t title the current note when a single window is open, because the first line of content typically supplies sufficient context. However, when opening notes in separate windows, the system titles them with the first line of content so people can tell them apart.

Don’t title windows with your app name. Your app’s name doesn’t provide useful information about your content hierarchy or any window or area in your app, so it doesn’t work well as a title.

Write a concise title. Aim for a word or short phrase that distills the purpose of the window or view, and keep the title under 15 characters long so you leave enough room for other controls.

Navigation
A toolbar with navigation controls appears at the top of a window, helping people move through a hierarchy of content. A toolbar also often contains a search field for quick navigation between areas or pieces of content. In iOS, a navigation-specific toolbar is sometimes called a navigation bar.

Use the standard Back and Close buttons. People know that the standard Back button lets them retrace their steps through a hierarchy of information, and the standard Close button closes a modal view. Prefer the standard symbols for each, and don’t use a text label that says Back or Close. If you create a custom version of either, make sure it still looks the same, behaves as people expect, and matches the rest of your interface, and ensure you consistently implement it throughout your app or game. For guidance, see Icons.

An illustration of a capsule-shape Back button that includes the Back symbol on the leading side, grouped with Back in text on the trailing side.

An X in a circle to indicate incorrect usage.

An illustration of the standard circular Back button that includes the standard Back symbol.

A checkmark in a circle to indicate correct usage.

Actions
Provide actions that support the main tasks people perform. In general, prioritize the commands that people are most likely to want. These commands are often the ones people use most frequently, but in some apps it might make sense to prioritize commands that map to the highest level or most important objects people work with.

Make sure the meaning of each control is clear. Don’t make people guess or experiment to figure out what a toolbar item does. Prefer simple, recognizable symbols for items instead of text, except for actions like edit that aren’t well-represented by symbols. For guidance on symbols that represent common actions, see Standard icons.

An illustration of an item group with text button labels for Filter, Delete, and New.

An X in a circle to indicate incorrect usage.

An illustration of an item group with symbol button labels for Filter, Delete, and New.

A checkmark in a circle to indicate correct usage.

Prefer system-provided symbols without borders. System-provided symbols are familiar, automatically receive appropriate coloring and vibrancy, and respond consistently to user interactions. Borders (like outlined circle symbols) aren’t necessary because the section provides a visible container, and the system defines hover and selection state appearances automatically. For guidance, see SF Symbols.

An illustration of an item group with buttons for Filter and More. The buttons are labeled with symbols with circular borders.

An X in a circle to indicate incorrect usage.

An illustration of an item group with buttons for Filter and More. The buttons are labeled with symbols without borders.

A checkmark in a circle to indicate correct usage.

Use the .prominent style for key actions such as Done or Submit. This separates and tints the action so there’s a clear focal point. Only specify one primary action, and put it on the trailing side of the toolbar.

An illustration of two toolbar items, with a Filter button on the leading side and a Done button on the trailing side. The buttons are ungrouped, and the Done button has the prominent style applied to indicate that it's the primary action.

Item groupings
You can position toolbar items in three locations: the leading edge, center area, and trailing edge of the toolbar. These areas provide familiar homes for navigation controls, window or document titles, common actions, and search.

Leading edge. Elements that let people return to the previous document and show or hide a sidebar appear at the far leading edge, followed by the view title. Next to the title, the toolbar can include a document menu that contains standard and app-specific commands that affect the document as a whole, such as Duplicate, Rename, Move, and Export. To ensure that these items are always available, items on the toolbar’s leading edge aren’t customizable.

Center area. Common, useful controls appear in the center area, and the view title can appear here if it’s not on the leading edge. In macOS and iPadOS, people can add, remove, and rearrange items here if you let them customize the toolbar, and items in this section automatically collapse into the system-managed overflow menu when the window shrinks enough in size.

Trailing edge. The trailing edge contains important items that need to remain available, buttons that open nearby inspectors, an optional search field, and the More menu that contains additional items and supports toolbar customization. It also includes a primary action like Done when one exists. Items on the trailing edge remain visible at all window sizes.

A diagram of the top toolbar in the Freeform app on iPad. Callouts indicate the location of item groupings on the leading edge, center area, and trailing edge of the toolbar.

To position items in the groupings you want, pin them to the leading edge, center, or trailing edge, and insert space between buttons or other items where appropriate.

Group toolbar items logically by function and frequency of use. For example, Keynote includes several sections that are based on functionality, including one for presentation-level commands, one for playback commands, and one for object insertion.

Group navigation controls and critical actions like Done, Close, or Save in dedicated, familiar, and visually distinct sections. This reflects their importance and helps people discover and understand these actions.

An illustration of a top toolbar on iPhone, with controls for back, forward, tool selection, and the More menu grouped in a single section on the trailing edge.

An X in a circle to indicate incorrect usage.

An illustration of a top toolbar on iPhone, with controls for back and forward grouped on the leading edge, and controls for tool selection and the More menu grouped on the trailing edge.

A checkmark in a circle to indicate correct usage.

Keep consistent groupings and placement across platforms. This helps people develop familiarity with your app and trust that it behaves similarly regardless of where they use it.

Minimize the number of groups. Too many groups of controls can make a toolbar feel cluttered and confusing, even with the added space on iPad and Mac. In general, aim for a maximum of three.

Keep actions with text labels separate. Placing an action with a text label next to an action with a symbol can create the illusion of a single action with a combined text and symbol, leading to confusion and misinterpretation. If your toolbar includes multiple text-labeled buttons, the text of those buttons may appear to run together, making the buttons indistinguishable. Add separation by inserting fixed space between the buttons. For developer guidance, see UIBarButtonItem.SystemItem.fixedSpace.

An illustration of a top toolbar on iPhone, with an Edit control with a text label and a Share control with a symbol grouped together on the trailing edge.

An X in a circle to indicate incorrect usage.

An illustration of a top toolbar on iPhone, with an Edit control with a text label and a Share control with a symbol grouped into individual sections on the trailing edge.

A checkmark in a circle to indicate correct usage.

Platform considerations
No additional considerations for tvOS.

iOS
Prioritize only the most important items for inclusion in the main toolbar area. Because space is so limited, carefully consider which actions are essential to your app and include those first. Create a More menu to include additional items.

Use a large title to help people stay oriented as they navigate and scroll. By default, a large title transitions to a standard title as people begin scrolling the content, and transitions back to large when people scroll to the top, reminding them of their current location. For developer guidance, see prefersLargeTitles.

iPadOS
Consider combining a toolbar with a tab bar. In iPadOS, a toolbar and a tab bar can coexist in the same horizontal space at the top of the view. This is particularly useful for layouts where you want to navigate between a few main app areas while keeping the full width of the window available for content. For guidance, see Layout and Windows.

macOS
In a macOS app, the toolbar resides in the frame at the top of a window, either below or integrated with the title bar. Note that window titles can display inline with controls, and toolbar items don’t include a bezel.

A diagram of a Finder window in macOS with callouts showing the location of the toolbar and the window frame.

Make every toolbar item available as a command in the menu bar. Because people can customize the toolbar or hide it, it can’t be the only place that presents a command. In contrast, it doesn’t make sense to provide a toolbar item for every menu item, because not all menu commands are important enough or used often enough to warrant space in the toolbar.

visionOS
In visionOS, the system-provided toolbar appears along the bottom edge of a window, above the window-management controls, and in a parallel plane that’s slightly in front of the window along the z-axis.

A screenshot of a toolbar along the bottom of the Photos app window in visionOS.

To maintain the legibility of toolbar items as content scrolls behind them, visionOS uses a variable blur in the bar background. The variable blur anchors the bar above the scrolling content while letting the view’s glass material remain uniform and undivided.

In visionOS, you can supply either a symbol or a text label for each toolbar item. When people look at a toolbar item that contains a symbol, visionOS reveals the text label, providing additional information.

Prefer using a system-provided toolbar. The standard toolbar has a consistent and familiar appearance and is optimized to work well with eye and hand input. In addition, the system automatically places a standard toolbar in the correct position in relation to its window.

A screenshot of a toolbar in visionOS.

Avoid creating a vertical toolbar. In visionOS, tab bars are vertical, so presenting a vertical toolbar could confuse people.

Try to prevent windows from resizing below the width of the toolbar. visionOS doesn’t include a menu bar where each app lists all its actions, so it’s important for the toolbar to provide reliable access to essential controls regardless of a window’s size.

If your app can enter a modal state, consider offering contextually relevant toolbar controls. For example, a photo-editing app might enter a modal state to help people perform a multistep editing task. In this scenario, the controls in the modal editing view are different from the controls in the main window. Be sure to reinstate the window’s standard toolbar controls when the app exits the modal state.

Avoid using a pull-down menu in a toolbar. A pull-down menu lets you offer additional actions related to a toolbar item, but can be difficult for people to discover and may clutter your interface. Because a toolbar is located at the bottom edge of a window in visionOS, a pull-down menu might obscure the standard window controls that appear below the bottom edge. For guidance, see Pull-down buttons.
