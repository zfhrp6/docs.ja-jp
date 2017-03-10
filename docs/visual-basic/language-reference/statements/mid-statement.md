---
title: "Mid Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.MidB"
  - "vb.Mid"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "substrings, Mid statement"
  - "strings [Visual Basic], substrings"
  - "Mid statement"
  - "strings [Visual Basic], replacing"
ms.assetid: 2b82d7a8-9646-4cb0-bec5-80abc98297bf
caps.latest.revision: 20
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 20
---
# Mid Statement
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

文字列型 \(`String`\) の変数内の指定した文字数分を別の文字列に置き換えます。  
  
## 構文  
  
```  
Mid( _  
   ByRef Target As String, _  
   ByVal Start As Integer, _  
   Optional ByVal Length As Integer _  
) = StringExpression  
```  
  
## 指定項目  
 `Target`  
 必ず指定します。  変更する文字列型 \(`String`\) の変数の名前です。  
  
 `Start`  
 必ず指定します。  整数型 \(`Integer`\) の式を指定します。  `Target` 内で、テキストの置換を開始する文字位置です。  `Start` のインデックスは 1 から始まります。  
  
 `Length`  
 省略可能です。  整数型 \(`Integer`\) の式を指定します。  置き換える文字数を指定します。  省略すると、`String` 全体が置き換えられます。  
  
 `StringExpression`  
 必ず指定します。  `Target` の該当部分を置き換える文字列型 \(`String`\) の式です。  
  
## 例外  
  
|例外の種類|状態|  
|-----------|--------|  
|<xref:System.ArgumentException>|`Start` \<\= 0 または `Length` \< 0 です。|  
  
## 解説  
 置換される文字数は、必ず `Target` の文字数以下になります。  
  
 Visual Basic には、<xref:Microsoft.VisualBasic.Strings.Mid%2A> 関数と `Mid` ステートメントがあります。  これらの要素はどちらも、文字列の中の指定された文字数を扱いますが、`Mid` 関数は文字を返すのに対し、`Mid` ステートメントは文字を置き換えます。  詳細については、「<xref:Microsoft.VisualBasic.Strings.Mid%2A>」を参照してください。  
  
> [!NOTE]
>  以前のバージョンの Visual Basic では、`MidB` ステートメントは文字数ではなくバイト数に基づいて部分文字列を置換していました。  これは主に、2 バイト文字セット \(DBCS\) アプリケーションで文字列を変換するために使用します。  Visual Basic のすべての文字列は Unicode で、`MidB` は現在サポートされていません。  
  
## 使用例  
 `Mid` ステートメントを使って、文字列変数内の指定された文字数をある文字列の文字に置き換える例を次に示します。  
  
 [!code-vb[VbVbalrStrings#5](../../../visual-basic/language-reference/functions/codesnippet/visualbasic/mid-statement_1.vb)]  
  
## 必要条件  
 **名前空間**: [Microsoft.VisualBasic](../../../visual-basic/language-reference/runtime-library-members.md)  
  
 **モジュール**: `Strings`  
  
 **アセンブリ**: [!INCLUDE[vbprvbruntime](../../../visual-basic/language-reference/objects/includes/vbprvbruntime-md.md)]  
  
## 参照  
 <xref:Microsoft.VisualBasic.Strings.Mid%2A>   
 [Strings](../../../visual-basic/programming-guide/language-features/strings/index.md)   
 [Introduction to Strings in Visual Basic](../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)