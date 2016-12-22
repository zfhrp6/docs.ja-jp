---
title: "is (C# リファレンス) | Microsoft Docs"
ms.custom: ""
ms.date: "12/03/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "is_CSharpKeyword"
  - "is"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "is キーワード [C#]"
ms.assetid: bc62316a-d41f-4f90-8300-c6f4f0556e43
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# is (C# リファレンス)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

オブジェクトと、指定した型との間に互換性があるかどうかをチェックします。  たとえば、次のコードでは、オブジェクトが `MyObject` 型のインスタンスか、または `MyObject` から派生した型か判定できます。  
  
```  
if (obj is MyObject)  
{  
}  
```  
  
 `is` 式は、指定した式が null 以外であり、指定したオブジェクトを指定した型に例外がスローされることなくキャストできる場合に、`true` と評価されます。  
  
 式が常に `true` または `false` であることがわかっている場合に `is` キーワードを使用すると、コンパイル時に警告が出力されますが、通常は、実行時の型の互換性が評価されます。  
  
 `is` 演算子はオーバーロードできません。  
  
 `is` 演算子では、参照変換、ボックス化変換、またはボックス化解除変換だけが考慮されます。  ユーザー定義変換など、他の変換は考慮されません。  
  
 匿名メソッドは、`is` 演算子の左辺では使用できません。  ラムダ式はその例外です。  
  
## 使用例  
 [!code-cs[csrefKeywordsOperator#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/is_1.cs)]  
  
## C\# 言語仕様  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## 参照  
 [C\# リファレンス](../../../csharp/language-reference/index.md)   
 [C\# プログラミング ガイド](../../../csharp/programming-guide/index.md)   
 [C\# のキーワード](../../../csharp/language-reference/keywords/index.md)   
 [typeof](../../../csharp/language-reference/keywords/typeof.md)   
 [as](../../../csharp/language-reference/keywords/as.md)   
 [演算子のキーワード](../../../csharp/language-reference/keywords/operator-keywords.md)