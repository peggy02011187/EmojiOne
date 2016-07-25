# Emoji

Emoji (絵文字えもじ?, Japanese pronunciation: [emodʑi]) are ideograms and smileys used in electronic messages and Web pages. The characters, which are used much like ASCII emoticons or kaomoji, exist in various genres, including facial expressions, common objects, places and types of weather, and animals.

# Emoji in text message 
Emoji in message will have pattern :    **:([-+\\w]+):**  
example :  :grinning:  --> 1f600

# To Replace all Emoji in message 
``` java    
 private static final HashMap<String, String> _shortNameToUnicode = new HashMap<String, String>();
 private static final Pattern SHORTNAME_PATTERN = Pattern.compile(":([-+\\w]+):");

    /**
     * Replace shortnames to unicode characters.
     */
    public static String shortnameToUnicode(String input, boolean removeIfUnsupported)
    {
        Matcher matcher = SHORTNAME_PATTERN.matcher(input);
        boolean supported = Build.VERSION.SDK_INT >= 16;

        while (matcher.find()) {
            String unicode = _shortNameToUnicode.get(matcher.group(1));
            if (unicode == null) {
                continue;
            }

            if (supported) {
                input = input.replace(":" + matcher.group(1) + ":", unicode);
            } else if (!supported && removeIfUnsupported) {
                input = input.replace(":" + matcher.group(1) + ":", "");
            }
        }

        return input;
    }
```

# unicode emoji 

   You cant consult in file  :  **Emojione.java** and **emoji.json**

