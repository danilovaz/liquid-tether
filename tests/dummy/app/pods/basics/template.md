<h1>The Basics</h1>

<p>
  Liquid Tether renders it's content near the application root and positions it
  using the <a href="http://tether.io/">Tether.js</a> library. However, the
  component retains its normal context within Ember, allowing it to communicate
  with surrounding components using attributes and actions.
</p>

<p>
  This allows you to embed your tethered objects anywhere in your code, meaning
  they can appear where they belong logically in your templates. You don't have
  to deal with any idiosyncratic services or APIs, and you don't have to worry
  about the peculiarities of positioning elements with CSS - It Just Works.
</p>

## Parameters

<p>
  Every Liquid Tether <strong>requires</strong> the following attributes:
</p>

<ul>
  <li>
    <strong>to</strong>: The name of the target-outlet that the
    tether will be attached to. The target is automatically
    instantiated and cleaned up as tethers are attached and removed from it.
  </li>
  <li>
    <strong>target</strong>: The selector of the element that the
    tether will be positioned relative to.
  </li>
  <li>
    <strong>attachment</strong>: The attachment point on the tethered
    element.
  </li>
</ul>

<p>
  Apart from the above required attributes, there is also one <strong>optional</strong>
  attribute:
</p>

<ul>
  <li>
    <strong>on-overlay-click</strong>: Action for handling clicking of the overlay. If the
    action is specified, the overlay also gets an additional class, i.e. 'clickable'.
  </li>
</ul>

<p>
  The following Tether.js options have also been mapped and can be
  passed in to Liquid Tether. Refer to the <a href="http://tether.io/">Tether.js
  documentation</a> for further details on their usage.
</p>

<ul>
  <li><strong>classPrefix</strong></li>
  <li><strong>offset</strong></li>
  <li><strong>targetAttachment</strong></li>
  <li><strong>targetOffset</strong></li>
  <li><strong>targetModifier</strong></li>
  <li><strong>constraints</strong></li>
  <li><strong>optimizations</strong></li>
</ul>

## Transitions

<p>
  Liquid Tether introduces the <code>target</code> constraint for matching
  targets by name and applying animations to them:
</p>

<div class="tab-content">
  <!-- {{code-snippet name="target-signature.js"}} -->
</div>

<p>
  It also adds the <code>onOpenTether</code> and <code>onCloseTether</code>
  constraints. These are quick constraints that you can add to give context to
  <code>use</code> and <code>reverse</code>. For instance, applying the
  <code>onOpenTether</code> constraint will apply the <code>use</code> animation
  to the tether as enters the dom, and the <code>reverse</code> animation to the
  tether as it leaves the dom.
</p>

<div class="tab-content">
  <!-- {{code-snippet name="open-tether-example.js"}} -->
</div>

<p>
  There are times when you may want to have knowledge of the context of
  your tethers. For instance, if you have a multi-step modal dialogue you may
  want to use different animations for the beginning of the dialogue, going to
  the next step, going to the previous step, and ending the dialogue. You can
  use the standard <code>toValue</code> and <code>fromValue</code> in these
  cases. The value passed into these elements is the <code>liquid-tether</code>
  component itself, so any values set on the tether will be comparable.
</p>

<div class="tab-content">
  <!-- {{code-snippet name="value-matching-example.hbs"}} -->
  <!-- {{code-snippet name="value-matching-example.js"}} -->
</div>

<p>
  In addition it includes the <code>tether</code> transition:
</p>

<div class="tab-content">
  <!-- {{code-snippet name="tether-transition-signature.js"}} -->
</div>

<p>
  which is a shorthand for the following <code>explode</code> transition:
</p>

<div class="tab-content">
  <!-- {{code-snippet name="tether-transition-code.js"}} -->
</div>

<p>
  While the <code>tether</code> transition should cover most standard use cases,
  there are times when it makes sense to use <code>explode</code> directly to
  animate tethered items. The <code>tether</code> transition receives two
  arguments, the transition to apply to the tethered element, and the transition
  to apply (if any) to the background overlay.
</p>

## DOM Structure and Styles

<p>
  Liquid Tether creates the following DOM structure:
</p>

<div class="tab-content">
  <!-- {{code-snippet name="tether-dom-structure.hbs"}} -->
</div>

<p>
  You can use the <code>overlayClass</code> and <code>tetherClass</code>
  properties to apply a class directly to either the overlay or the tethered
  element. You can also apply a class directly to the liquid-destination that
  contains your tethered element using the <code>targetClass</code> property.
</p>

## Ember Compatibility

<p>
  Liquid Tether is tested on all versions of Ember >= 1.13. Long term support will
  continue for 1.13 and up for as long Ember core support continues.
</p>
