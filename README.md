# Grondals Impact Docs

In the following, you find all code changes to the Grondals webshop.

## Header

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

## Product Card