---
title: "Typographic and Code Conventions (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "coding conventions, Visual Basic"
  - "best practices, coding conventions"
  - "conventions, Visual Basic coding"
  - "typographic conventions"
  - "document conventions"
  - "conventions, documentation"
  - "Visual Basic code, conventions"
ms.assetid: 1916cd81-ea9d-4faa-81f7-4a0d864b60f4
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Typographic and Code Conventions (Visual Basic)
[!INCLUDE[vs2017banner](../../visual-basic/developing-apps/includes/vs2017banner.md)]

Visual Basic のヘルプは、次の表記規則とコード規則に従って記述されています。  
  
## 表記規則  
  
|例|Description|  
|-------|-----------------|  
|`Sub`, `If`, `ChDir`, `Print`, `True`, `Debug`|言語特有のキーワードやランタイム メンバーは、先頭が大文字になっており、この例に示す書式が使用されています。|  
|SmallProject、ButtonCollection|ユーザーが入力する語および句には、この例に示す書式が使用されています。|  
|[Module Statement](../../visual-basic/language-reference/statements/module-statement.md)|クリックすると他のヘルプ ページに移動するリンクには、この例に示す書式が使用されています。|  
|*object*、*variableName*、`argumentList`|ユーザーが入力する情報のプレースホルダーには、この例に示す書式が使用されています。|  
|\[ Shadows \]、\[ *expressionList* \]|構文内の省略可能な項目は、角かっこで囲まれています。|  
|{ `Public` &#124; `Friend` &#124; `Private` }|構文内で、複数の項目から 1 つを選択する必要がある場合は、項目が中かっこで囲まれ、縦棒で区切られています。<br /><br /> 1 つの項目だけを選択する必要があります。|  
|\[ `Protected` &#124; `Friend` \]|構文内で、複数の項目から選択可能な場合は、項目が角かっこで囲まれ、縦棒で区切られています。<br /><br /> これらの項目を任意に組み合わせて選択するか、または何も選択しないこともできます。|  
|\[{ `ByVal` &#124; `ByRef` }\]|構文内で、項目を 1 つだけ選択するか、何も選択しないこともできる場合は、項目が中かっこを囲む角かっこで囲まれ、縦棒で区切られています。|  
|*memberName* 1、*memberName*2、*memberName*3|同じプレースホルダーの複数のインスタンスは、この例に示すように添字によって区別されます。|  
|*memberName1*<br /><br /> ...<br /><br /> *memberNameN*|構文内の省略記号 \(...\) は、省略記号の直前の種類の項目が無限に続くことを示します。<br /><br /> コードでは、わかりやすくするために省略されたコードを示します。|  
|ESC、ENTER|キーボードのキー名やキー シーケンスは、すべて大文字で表記されます。|  
|Alt \+ F1|キー名の間にプラス記号 \(\+\) がある場合、一方のキーを押したままでもう一方のキーを押す必要があります。  たとえば、Alt \+ F1 は Alt キーを押しながら、F1 キーを押すことを表します。|  
  
## コード規則  
  
|例|Description|  
|-------|-----------------|  
|`sampleString = "Hello, world!"`|コード サンプルは、固定ピッチ フォントで表記され、この例に示す書式になっています。|  
|このステートメントは、`sampleString` の値を "Hello, world\!" に設定します。|解説文に含まれるコード要素は、この例に示すように固定ピッチ フォントで表記されます。|  
|`' This is a comment.`<br /><br /> `REM This is also a comment.`|コードのコメントは、アポストロフィ \('\) や REM キーワードで始まります。|  
|`sampleVar = "This is an " _`<br /><br /> `& "example" _`<br /><br /> `& " of how to continue code."`|行末の空白とアンダースコア \( \_\) は、ステートメントが次の行に継続することを示します。|  
  
## 参照  
 [Visual Basic Language Reference](../../visual-basic/language-reference/index.md)   
 [キーワード](../../visual-basic/language-reference/keywords/index.md)   
 [Visual Basic Runtime Library Members](../../visual-basic/language-reference/runtime-library-members.md)   
 [Visual Basic Naming Conventions](../../visual-basic/programming-guide/program-structure/naming-conventions.md)   
 [方法 : コード内でステートメントを分割および連結する](../../visual-basic/programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)   
 [Comments in Code](../../visual-basic/programming-guide/program-structure/comments-in-code.md)