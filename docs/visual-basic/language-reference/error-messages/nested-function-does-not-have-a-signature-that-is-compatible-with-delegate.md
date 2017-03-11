---
title: "Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39; | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc36532"
  - "bc36532"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC36532"
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 5
---
# Nested function does not have a signature that is compatible with delegate &#39;&lt;delegatename&gt;&#39;
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

シグネチャが対応していないデリゲートにラムダ式が割り当てられています。  たとえば、次のコードでは、デリゲート `Del` に 2 つの整数パラメーターがあります。  
  
```vb#  
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer  
```  
  
 引数が 1 つしかないラムダ式を `Del` 型として宣言すると、エラーになります。  
  
```vb#  
' Neither of these is valid.   
' Dim lambda1 As Del = Function(n As Integer) n + 1  
' Dim lambda2 As Del = Function(n) n + 1  
```  
  
 **エラー ID:** BC36532  
  
### このエラーを解決するには  
  
-   シグネチャが対応するように、デリゲート定義または割り当てるラムダ式のいずれかを変更します。  
  
## 参照  
 [Relaxed Delegate Conversion](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)   
 [Lambda Expressions](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)