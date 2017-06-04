---
title: "セキュリティとパブリックの読み取り専用配列フィールド | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "セキュリティ [.NET Framework], パブリックの読み取り専用配列フィールド"
ms.assetid: 3df28dee-2a9f-40ff-9852-bfdbe59c27f3
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# セキュリティとパブリックの読み取り専用配列フィールド
読み取り専用のパブリック配列フィールドは変更できるため、マネージ ライブラリから読み取り専用のパブリック配列フィールドを使用して、アプリケーションの境界動作やセキュリティを定義しないでください。  
  
## 解説  
 .NET Framework の一部のクラスには、プラットフォーム固有の境界パラメーターを含む読み取り専用のパブリック フィールドが含まれます。たとえば <xref:System.IO.Path.InvalidPathChars> フィールドは、ファイル パス文字列で使用できない文字を記述する配列です。.NET Framework には、これに類似したフィールドが数多くあります。  
  
 <xref:System.IO.Path.InvalidPathChars> などのパブリックの読み取り専用フィールドの値は、コード、またはコードのアプリケーション ドメインを共有するコードを使用して変更できます。このような読み取り専用のパブリック配列フィールドを使用して、アプリケーションの境界動作を定義しないでください。このようなフィールドを使用してアプリケーションの境界動作を定義すると、悪意のあるコードによって境界定義が変更され、コードが悪用される恐れがあります。  
  
 .NET Framework Version 2.0 以降では、パブリック配列フィールドを使用する代わりに、新しい配列を返すメソッドを使用します。たとえば、<xref:System.IO.Path.InvalidPathChars> フィールドを使用する代わりに <xref:System.IO.Path.GetInvalidPathChars%2A> メソッドを使用します。  
  
 .NET Framework の型は、パブリック フィールドを使用して境界の種類を内部的に定義しないことに注意してください。代わりに .NET Framework では、個別のプライベート フィールドを使用します。パブリック フィールドの値を変更しても、.NET Framework の型の動作は変わりません。  
  
## 参照  
 [安全なコーディングのガイドライン](../../../docs/standard/security/secure-coding-guidelines.md)