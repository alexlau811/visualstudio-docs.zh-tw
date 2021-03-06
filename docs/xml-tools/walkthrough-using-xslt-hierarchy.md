---
title: 逐步解說：使用 XSLT 階層
ms.date: 11/04/2016
ms.prod: visual-studio-dev15
ms.technology: vs-xml-tools
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 20223a18fa422facc7d7a0a74336402d6d391b0a
ms.sourcegitcommit: 0aafcfa08ef74f162af2e5079be77061d7885cac
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2018
ms.locfileid: "34693441"
---
# <a name="walkthrough-use-xslt-hierarchy"></a>逐步解說： 使用 XSLT 階層

XSLT 階層工具可簡化許多 XML 開發工作。 XSLT 樣式表經常使用 `includes` 和 `imports` 指示。 編譯會從主樣式表開始，但當您看見編譯 XSLT 樣式表所產生的錯誤時，該錯誤的來源可能並非主要樣式表。 修復錯誤或編輯樣式表可能需要存取包含或匯入的樣式表。 在偵錯工具中逐步執行樣式表會開啟包含及匯入的樣式表，您可以在一個或多個包含的樣式表中加入一些中斷點。

另一個可利用 XSLT 階層工具的案例，是在內建的範本規則中放置中斷點。 範本規則是針對樣式表的每種模式所產生的特殊範本，若沒有其他範本與節點相符，`xsl:apply-templates` 就會呼叫範本規則。 為了在內建範本規則中實作偵錯，XSLT 偵錯工具會在暫存資料夾中產生含有規則的檔案，然後將檔案與主樣式表一起編譯。 若未從某個 `xsl:apply-template` 逐步執行程式碼，可能不容易找到已包含在主樣式表中的樣式表，也不容易找到並開啟含有內建範本規則的樣式表。

本主題中的範例將示範參考的樣式表中的偵錯。

## <a name="to-debug-in-a-referenced-style-sheet"></a>在參考的樣式表中偵錯

1. 在 Visual Studio 中開啟 XML 文件。 這個範例會使用下列文件：

    ```xml
    <?xml version="1.0" encoding="utf-8"?>
    <?xml-stylesheet type="text/xsl" href="xslinclude.xsl"?>
    <COLLECTION>
      <BOOK>
        <TITLE>Lover Birds</TITLE>
        <AUTHOR>Cynthia Randall</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>The Sundered Grail</TITLE>
        <AUTHOR>Eva Corets</AUTHOR>
        <PUBLISHER>Lucerne Publishing</PUBLISHER>
      </BOOK>
      <BOOK>
        <TITLE>Splish Splash</TITLE>
        <AUTHOR>Paula Thurman</AUTHOR>
        <PUBLISHER>Scootney</PUBLISHER>
      </BOOK>
    </COLLECTION>
    ```

1. 加入下列*xslincludefile.xsl*:

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform"
          xml:space="preserve">

    <xsl:template match="TITLE">
       Title - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="AUTHOR">
       Author - <xsl:value-of select="."/><BR/>
    </xsl:template>

    <xsl:template match="PUBLISHER">
       Publisher - <xsl:value-of select="."/><BR/><!-- removed second <BR/> -->
    </xsl:template>

    </xsl:stylesheet>
    ```

3.  加入下列*xslinclude.xsl*檔案：

    ```xml
    <?xml version='1.0'?>
    <xsl:stylesheet version="1.0"
          xmlns:xsl="http://www.w3.org/1999/XSL/Transform">

      <xsl:output method="xml" omit-xml-declaration="yes"/>

      <xsl:template match="/">
        <xsl:for-each select="COLLECTION/BOOK">
          <xsl:apply-templates select="TITLE"/>
          <xsl:apply-templates select="AUTHOR"/>
          <xsl:apply-templates select="PUBLISHER"/>
          <BR/>
          <!-- add this -->
        </xsl:for-each>
      </xsl:template>

      <!-- The following template rule will not be called,
      because the related template in the including stylesheet
      is called. If we move this template so that
      it follows the xsl:include instruction, this one
      will be called instead.-->
      <xsl:template match="TITLE">
        <DIV STYLE="color:blue">
          Title: <xsl:value-of select="."/>
        </DIV>
      </xsl:template>

      <xsl:include href="xslincludefile.xsl" />
    </xsl:stylesheet>
    ```

4.  在指令處加入中斷點`<xsl:include href="xslincludefile.xsl" />`。

5.  開始偵錯。

6.  偵錯工具停在指示`<xsl:include href="xslincludefile.xsl" />`，按**逐步執行** 按鈕。 在參考的樣式表可以繼續偵錯。 您會看見階層，同時設計工具會顯示正確的路徑。

## <a name="see-also"></a>另請參閱

- [逐步解說： XSLT 分析工具](../xml-tools/walkthrough-xslt-profiler.md)