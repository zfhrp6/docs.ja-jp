---
title: "Directives (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "directives, Visual Basic compiler"
  - "Visual Basic code, directives"
  - "directives"
ms.assetid: 20d5fe65-490a-4c23-88c2-ee4f490ed762
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Directives (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

このセクションのトピックでは、Visual Basic ソース コードのコンパイラ ディレクティブについて説明します。  
  
## このセクションの内容  
 [\#Const Directive](../../../visual-basic/language-reference/directives/const-directive.md) \-\- コンパイラ定数を定義します  
  
 [\#ExternalSource Directive](../../../visual-basic/language-reference/directives/externalsource-directive.md) \-\- ソース行とソース外部のテキストのマッピングを指定します  
  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md) \-\- 選択したコード ブロックをコンパイルします  
  
 [\#Region Directive](../../../visual-basic/language-reference/directives/region-directive.md) \-\- Visual Studio エディターでコードのセクションを折りたたんで非表示にします  
  
 **\#Disable、\#Enable** \-\- コードの領域に対して特定の警告を無効および有効にします。  
  
```vb  
#Disable Warning BC42356 ' suppress warning about no awaits in this method  
    Async Function TestAsync() As Task  
        Console.WriteLine("testing")  
    End Function  
#Enable Warning BC42356  
  
```  
  
 警告コードのコンマ区切りリストを無効および有効にすることもできます。  
  
## 関連項目  
 [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md)  
  
 [Visual Basic](../../../visual-basic/index.md)