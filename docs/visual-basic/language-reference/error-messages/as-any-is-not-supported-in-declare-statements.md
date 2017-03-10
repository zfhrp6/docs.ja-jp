---
title: "&#39;As Any&#39; is not supported in &#39;Declare&#39; statements | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30828"
  - "vbc30828"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30828"
ms.assetid: 7e5cf519-8b64-4ac5-8116-705fe26c846d
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &#39;As Any&#39; is not supported in &#39;Declare&#39; statements
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

`Any` 型は、Visual Basic 6.0 以前のバージョンの `Declare` ステートメントで、任意のデータ型を受け取ることができる引数を宣言するために使用されていました。  しかし、[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] でオーバーロードがサポートされたため、`Any` 型は使用されなくなりました。  
  
 **Error ID:** BC30828  
  
### このエラーを解決するには  
  
1.  使用する特定の型のパラメーターを宣言します。次に例を示します。  
  
     [!code-vb[VbVbalrStatements#95](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/as-any-is-not-supported-_1.vb)]  
  
2.  呼び出しているプロシージャで `Void*` が必要とされている場合は、<xref:System.Runtime.InteropServices.MarshalAsAttribute> 属性を使用して `As Any` を指定します。  
  
     [!code-vb[VbVbalrStatements#96](../../../visual-basic/language-reference/error-messages/codesnippet/visualbasic/as-any-is-not-supported-_2.vb)]  
  
## 参照  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Walkthrough: Calling Windows APIs](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)   
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)   
 [マネージ コードでのプロトタイプの作成](../Topic/Creating%20Prototypes%20in%20Managed%20Code.md)