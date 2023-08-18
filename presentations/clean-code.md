---
theme: uncover
class:
  - lead
  - invert
marp: true
---

![bg left:40% 80%](../assets/icons/books.svg)

# Clean Code

Crucial code skills.

---

### What?

![](../assets/images/presentation-coding.gif)

---

### What?

"A school of thought".

---

### What?

"There's Hakkoryu's Jiu-Jitsu and Gracie's Jiu-Jitsu..."

---

### To whom?

Not recommended to beginners.

---

### Chapters

- Clean code
- Significant names
- Concurrence
- Function
- Successive refinement
- Smells and Heuristics
- Unit testing

And so much more...

---

### The productivity issue

1. You have to deal with other person's code that is confusing
2. There's a significant delay while developing
3. The code changes break 2 or 3 parts of the code, you have to deal with them
4. Time passes and the mess is still growing
5. Your team slows on productivity
6. The managers hire more developers
7. The mess still grows and the productivity almost goes to zero

---

### The replanning issue

1. The dev team rebels against the managers, demanding a replanning
2. The managers say "Ok, the productivity is awful"
3. The super dev team is created to solve the productivity issue
4. The super team is in a rush to create the new software, just as the dev team
5. The super team starts leaving the company
6. The company goes back to the productivity issue

---

Protect the code with your passion!

---

## Significant names

Reveal the purpose, avoid mind mapping

Bad

```
int d // days after purchase
int days
```

Good

```
int daysAfterPurchase;
```

---

### Significant names

One word for each concept, not for different ideas. "Don't try to be a smart guy."

Bad

```
public void insertUser(User user)
public void registerCategory(TransactionCategory category)
public void pushFinancialTransaction(Transaction transaction)
```

Good

```
public void saveUser(User user)
public void saveCategory(TransactionCategory category)
public void saveFinancialTransaction(Transaction transaction)
```

---

### Functions

First rule! They have to be small. Maximum of 20 lines, "but they should have 2,3, or 4"

---

### Functions - example

```
public static String renderPagewithSetupsAndTeardowns (
    PageData pageData, boolean isSuite
) throws Exception {
    boolean isTestPage = pageData.hasAttribute ("Test*) ;
    if (isTestPage) (
        WikiPage testPage = pageData.getWikiPage();
        StringBuffer newPageContent = new StringBuffer();
        includeSetupPages(testPage, newPageContent, isSuite);
        newPageContent.append(pageData.getContent());
        includeTeardownPages(testPage, newPageContent, isSuite);
        pageData.setContent(newPageContent.toString());
    )
    return pageData.getHtml();
}
```

---

### Functions - example

Instructions like _if_, _else_, _while_ should have only one line.

```
public static String render PagewithSetupsAndTeardowns(PageData pageData, boolean isSuite) throws Exception (
        if (isTestPage(pageData))
            includeSetupAndTeardownPages(pageData, isSuite);
    return pageData.getHtml();
}
```

---

### Comments

"Don't write comments in a bad code, rewrite it"
-Brian W. Kernighan e P. J. Plaugher

--

"Comments are, at maximum, a necessary evil"
-Robert C. Martin

--

"Commments compensate your failure"
-Robert C. Martin

---

### Comments

Some good examples

- Copyright
- TODO:
- Importance: "This function avoids a bug caused by the library"

---

### Formatting

- Vertical formatting: Max of 200-500 lines per file
- Vertical formatting: If a functions calls another, they should be vertically next to each other
- Horizontal formatting: use white space to associate things alike
- Horizontal formatting: 120 lines. You're not being careful if you're surpassing this

---

### Error handling

- Use try-catch-finally for possible exceptions
- Never return null
- Provide exceptions with a context, and also a message

---

### Unit tests

- TDD
- One affirmation for each test
- Clean tests

---

### Unit tests - Example

```
public void testGetPageHierarchyAsXml() throws Exception
        crawler.addPage(root, PathParser.parse("PageOne"));
        crawler.addPage(root, PathParser.parse("PageOne.ChildOne"));
        crawler.addPage(root, PathParser.parse("PageTwo"));

        request.setResource("root");
        request.addInput("type", "pages");

        Responder responder = new SerializedPageResponder();
        SimpleResponse response = (SimpleResponse) responder.makeResponse (new FitNesseContext(root), request);
        String xml = response.getContent();

        assertEquals(*text/xml", , response.getContentType());
        assertSubString("<name>PageOne</name>", xml);
        assertSubString("<name>PageTwo</name>', xml);
        assertSubString('<name>ChildOne</name>*, xml);
    }
```

---

## Unit tests - Clean Test Example

```
public void testGetPageHierarchyAsXml () throws Exception {
    makePages("PageOne", "PageOne.ChildOne", "PageTwo");

    submitRequest('root", "type :pages");

    assertResponseIsXML();
    assertResponseContains('«name> PageOne</name>","<name>PageTwo</name›', "<name>ChildOne</name>");
}
```

---

### Why?

![](../assets/images/presentation-coding.gif)

---

### Why?

You're a developer that wants to be a better developer.

---

![](../assets/images/presentation-thanks.gif)
