---
title: "使用方法のガイドライン | Microsoft Docs"
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
  - "クラス ライブラリ デザインのガイドライン [.NET Framework] の使用に関するガイドライン"
ms.assetid: 42215ffa-a099-4a26-b14e-fb2bdb6f95b7
caps.latest.revision: 9
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 9
---
# 使用方法のガイドライン
このセクションには、パブリックにアクセスできる Api で一般的な種類の使用に関するガイドラインが含まれています。 組み込みフレームワーク型 \(シリアル化属性など\) および一般的な演算子のオーバー ロードの直接の使用状況を処理します。  
  
 <xref:System.IDisposable?displayProperty=fullName> インターフェイスは、このセクションで説明されていないは、後ほど、 [Dispose パターン](../../../docs/standard/design-guidelines/dispose-pattern.md) セクションです。  
  
> [!NOTE]
>  組み込みの .NET Framework 型のガイドラインと他の一般的な方法に関する追加情報には、次のリファレンス トピックを参照してください: <xref:System.DateTime?displayProperty=fullName>, 、<xref:System.DateTimeOffset?displayProperty=fullName>, 、<xref:System.ICloneable?displayProperty=fullName>, 、<xref:System.IComparable%601?displayProperty=fullName>, 、<xref:System.IEquatable%601?displayProperty=fullName>, 、<xref:System.Nullable%601?displayProperty=fullName>, 、<xref:System.Object?displayProperty=fullName>, 、<xref:System.Uri?displayProperty=fullName>です。  
  
## このセクションの内容  
 [配列](../../../docs/standard/design-guidelines/arrays.md)  
 [属性](../../../docs/standard/design-guidelines/属性.md)  
 [コレクション クラス](../../../amples/snippets/cpp/VS_Snippets_Misc/cx_collections/cpp/collections.vcxproj)  
 [シリアル化](../../../docs/standard/design-guidelines/シリアル化.md)  
 [System.Xml の使用法](../../../docs/standard/design-guidelines/system-xml-usage.md)  
 [等値演算子](../../../docs/standard/design-guidelines/equality-operators.md)  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)