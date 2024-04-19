# Grondals Impact Docs

In the following, you find all code changes to the Grondals webshop.

## Header
1. Disabled account-icon. Delete ```style="display: none"``` if you want to get the icon back on the shop

```
<a href="{% if customer %}{{ routes.account_url }}{% else %}{{ routes.account_login_url }}{% endif %}" class="hidden tap-area sm:block" style="display: none;">
```
## Footer

Add payment icons to the footer

1. Add this line of code to the first line

```
{%- assign paymentIconsFix = "mobilepay,dankort,visa,master,klarna,maestro,apple_pay" | split: "," -%}
```

2. Find shop.enabled_payment_types and replace it with paymentIconFix. It should look like this code snippet:

````
    {%- if section.settings.show_payment_icons and paymentIconsFix.size > 0 -%}
            <div class="footer__payment-icons h-stack wrap gap-2">
            {%- for type in paymentIconsFix -%}
                {{- type | payment_type_svg_tag -}}
            {%- endfor -%}
            </div>
    {%- endif -%}
````

3. Don't forget to enable Payment Icons in the Editor!

## Cart Drawer (Mini Cart)
Insert on the first line:
```
{%- assign paymentIconsFix = "mobilepay,dankort,visa,master,klarna,maestro,apple_pay" | split: "," -%}
```

...and just right before the closing </div>

```
<div class="footer__payment-icons h-stack wrap gap-2" style="justify-content: center;">
    {%- for type in paymentIconsFix -%}
    {{- type | payment_type_svg_tag -}}
    {%- endfor -%}
</div>  
```
## Accordion Content 
Replace border with wave-image. Add background image to **.accordion__toggle** 

````
    .accordion__toggle {
  gap: var(--spacing-2);
  flex-grow: 1;
  justify-content: space-between;
  align-items: center;
  padding-block-start: var(--accordion-spacing);
  padding-block-end: var(--accordion-spacing);
  display: flex;
  border-bottom: none;
  border-color: transparent;
  background-repeat: repeat-x;
  background-size: 272% 9px;
  background-image:url('../assets/grondals-bolge-petroleum.png');
}
@media screen and (max-width: 500px) {
    .accordion__toggle {
      background-size: 211% 4px;
    }
}
````
## Product Card
1. Add block setting to *featured-product.liquid*

```
{
      "type": "logo_text_block",
      "name": "Logo Text Block"
}
```
2. Change "Beskrivelse" to "Produktinformation" in locales/da.json
````
     "description": "Om Produktet"
````