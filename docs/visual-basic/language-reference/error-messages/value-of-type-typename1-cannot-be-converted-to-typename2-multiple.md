---
title: "Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbc30961"
  - "bc30961"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30961"
ms.assetid: 8be5aa0d-d236-4ac3-aa9c-5044f9f6562b
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Value of type &#39;&lt;typename1&gt;&#39; cannot be converted to &#39;&lt;typename2&gt;&#39; (Multiple file references)
[!INCLUDE[vs2017banner](../../../visual-basic/developing-apps/includes/vs2017banner.md)]

型 '\<typename1\>' の値を '\<typename2\>' に変換できません。型の不一致は、プロジェクト '\<projectname1\>' の '\<filepath1\>' へのファイル参照とプロジェクト '\<projectname2\>' の '\<filepath2\>' へのファイル参照との混合によって生じた可能性があります。両方のアセンブリが同一である場合は、同じ場所から参照するようにこれらの参照を置き換えてください。  
  
 プロジェクトで同じアセンブリへの複数のファイル参照が作成される場合、コンパイラは型が別の型に正しく変換されることを保証できません。  
  
 それぞれのファイル参照は、プロジェクトの出力ファイルのファイル パスおよび名前を指定しています \(通常は DLL ファイル\)。  コンパイラは、出力ファイルが同じソースから得られることも、それらが同じアセンブリの同じバージョンを表していることも保証できません。  したがって、異なる参照内の型が同じ型であることも、ある型を他の型に変換できることも保証できません。  
  
 複数の参照アセンブリのアセンブリ ID が同じであることがわかっている場合は、単一のファイル参照を使用できます。  *アセンブリ ID* には、アセンブリの名前、バージョン、公開キー \(公開キーがある場合\)、およびカルチャが含まれます。  この情報により、アセンブリを一意に識別します。  
  
 **Error ID:** BC30961  
  
### このエラーを解決するには  
  
-   複数の参照アセンブリのアセンブリ ID が同じ場合は、一方のファイル参照を削除するか置き換えて、単一のファイル参照だけにします。  
  
-   複数の参照アセンブリのアセンブリ ID が同じではない場合は、コードを変更して、一方のアセンブリの型を他方のアセンブリの型に変換しないようにします。  
  
## 参照  
 [Type Conversions in Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)   
 [プロジェクト内の参照の管理](/visual-studio/ide/managing-references-in-a-project)   
 [方法: &#91;参照の追加&#93; ダイアログ ボックスを使用して参照を追加または削除する](http://msdn.microsoft.com/ja-jp/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)