# Create a new Jackson Property Naming Strategy that convers _ to CamelCase

I needed a new strategy to automatically convert user_name to userName.
I took a look at the code behind the PropertyNamingStrategy class and found the code that do the translations.

here it is a simple class that does the job. useful if you have your hibernate bean properties with _ inside them and you don't want to put lots of JsonIgnore annotations.

```java
import com.fasterxml.jackson.databind.PropertyNamingStrategy.PropertyNamingStrategyBase;
public static class CustomCamelCaseStrategy extends PropertyNamingStrategyBase {
    @Override
    public String translate(String input) {
        if (input == null) {
            return input; // garbage in, garbage out
        }
        int length = input.length();
        StringBuilder result = new StringBuilder(length);
        int resultLength = 0;
        boolean wasPrevTranslated = false;
        for (int i = 0; i < length; i++) {
            char c = input.charAt(i);
            if (c == '_') {
                if (i < length - 1) {
                    if (i == 0) {
                        result.append(Character.toLowerCase(input.charAt(i + 1)));
                    } else {
                        result.append(Character.toUpperCase(input.charAt(i + 1)));
                    }
                    resultLength++;
                }
                wasPrevTranslated = true;
            } else {
                if (!wasPrevTranslated) {
                    result.append(c);
                    resultLength++;
                }
                wasPrevTranslated = false;
            }
        }
        return resultLength > 0 ? result.toString() : input;
    }
}
```