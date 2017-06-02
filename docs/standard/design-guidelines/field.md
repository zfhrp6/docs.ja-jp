---
title: "フィールドのデザイン | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "フィールドのデザイン ガイドライン"
  - "読み取り専用フィールド"
  - "メンバー デザインのガイドライン、フィールド"
ms.assetid: 7cb4b0f3-7a10-4c93-b84d-733f7134fcf8
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# フィールドのデザイン
カプセル化の原理は、オブジェクト指向設計に最も重要な概念の 1 つです。 この原則は、オブジェクト内に格納されているデータはそのオブジェクトにのみアクセスできることを示しています。  
  
 原則を解釈する便利な方法は以外のコードを型のメンバーを損なうことがなくその型 \(名前または種類の変更\) のフィールドへの変更ができるように、型を設計する必要があります。 すぐに、この解釈は、プライベートのすべてのフィールドである必要がありますを意味します。  
  
 必要であるため、このようなフィールドほとんど定義では、決してを変更する、この厳密な制限から定数と静的な読み取り専用フィールドを除外しました  
  
 **X のしないで** パブリックまたはプロテクト インスタンス フィールドを提供します。  
  
 パブリックまたはプロテクトにする代わりにフィールドにアクセスするためのプロパティを指定する必要があります。  
  
 **✓ は** 定数フィールドは決して変化しない定数に使用します。  
  
 コンパイラは、const フィールドの値を直接コードを呼び出す焼き付けます。 そのため、const 値は、互換性の問題の危険を回避しない変更できます。  
  
 **✓ は** のパブリック静的を使用して `readonly` フィールドの定義済みのオブジェクト インスタンス。  
  
 型の定義済みのインスタンスがある場合により読み取り専用で、型自体の静的フィールドをパブリックとしてと宣言します。  
  
 **X のしないで** に変更可能な型のインスタンスを割り当てる `readonly` フィールドです。  
  
 変更可能な型は、オブジェクトのインスタンスは後で変更できるインスタンスの型です。 たとえば、配列、ほとんどのコレクション、およびストリームは変更可能な型が、 <xref:System.Int32?displayProperty=fullName>, 、<xref:System.Uri?displayProperty=fullName>, 、および <xref:System.String?displayProperty=fullName> はすべて不変です。 参照型のフィールドに対する読み取り専用修飾子には、置き換えられるのフィールドに格納されているインスタンスができなくなりますが、フィールドのインスタンス データのインスタンスを変更するメンバーを呼び出すことによって変更を妨げることはできません。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [メンバー デザインのガイドライン](../../../docs/standard/design-guidelines/member.md)   
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)