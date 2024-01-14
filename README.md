
# Somes Shopify Themes Improvement


#### This project is kind of a personal cheat sheet for Shopify. This is not my job, so I thought it will be more easy for me to remember this if I share it on GitHub

### Free to use at your own risk, I do not offer support of any kind.

### Please duplicate (backup) your theme before doing anythings.
- [How to backup my theme code?](https://help.shopify.com/en/manual/online-store/themes/managing-themes/duplicating-themes)

- [How to edit my theme code?](https://help.shopify.com/en/manual/online-store/themes/theme-structure/extend/edit-theme-code)

## Select variants by clicking their images (Dawn 11.0.0)

### Media-gallery.js
####  In the setActiveMedia(mediaId, prepend) function add this line
```bash
this.updateVariant(this.getProductId(mediaId),this.getVariantId(mediaId))

```
####  Add the end of the class add these lines of code
```bash
getProductId(rawId){
        rawId = rawId.substring(0,rawId.indexOf("_"));
        return rawId.substring(10,rawId.length);
      }
getVariantId(rawId){
        rawId = rawId.substring(rawId.indexOf("main-"),rawId.length);
        return rawId.substring(5,rawId.length);
      }
//Click on the hiden radio buttons       
updateVariant(productId,variantId){
        var variantRadioButton = document.getElementById("variant-radios-template--"+productId+"__main");
        if(variantRadioButton != null){
          for(var variant of variantRadioButton.getVariantData()){
            if(`${variant.featured_media.id}` == variantId){
              var value = variant.option1
              for(var child of variantRadioButton.children[0].children)
                if(child.value == value){
                  child.click()
                }
            }
          }
        }
      }
```

#### You are now able to select a variant by clicking on his own image
## To be continued...
