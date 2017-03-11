---
title: "DLL のクライアント アプリケーションの数が多すぎます | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID47"
ms.assetid: 4b87780b-67ad-4c96-9253-db954a751dad
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# DLL のクライアント アプリケーションの数が多すぎます
[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] のダイナミック リンク ライブラリ \(DLL\) にアクセスできるホスト アプリケーションの数は限られています。 使用しているアプリケーションと、[!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] ホスト \(その一部は使用しているアプリケーションによってアクセスされる可能性があります\) であるその他のアプリケーションとがすべて同時に [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] DLL にアクセスしようとしています。  
  
### このエラーを解決するには  
  
-   [!INCLUDE[vbprvb](../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] にアクセスする動作中のアプリケーションの数を減らします。  
  
## 参照  
 [Error Types](../../visual-basic/programming-guide/language-features/error-types.md)