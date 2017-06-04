---
title: "System.Xml の使用法 | Microsoft Docs"
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
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 4
---
# System.Xml の使用法
このセクションでに存在するいくつかの型の使用方法について説明 <xref:System.Xml?displayProperty=fullName> XML データを表現するために使用する名前空間。  
  
 **X のしないで** を使用して <xref:System.Xml.XmlNode> または <xref:System.Xml.XmlDocument> XML データを表現します。 インスタンスの使用をお勧め <xref:System.Xml.XPath.IXPathNavigable>, 、<xref:System.Xml.XmlReader>, 、<xref:System.Xml.XmlWriter>, 、または型を細分化 <xref:System.Xml.Linq.XNode> 代わりにします。`XmlNode``XmlDocument` パブリック Api で公開するために設計されていません。  
  
 **✓ は** を使用して `XmlReader`, 、`IXPathNavigable`, 、または型を細分化 `XNode` メンバーや XML を戻り値の入力または出力として。  
  
 代わりにこれらの抽象化を使用して `XmlDocument`, 、`XmlNode`, 、または <xref:System.Xml.XPath.XPathDocument>, を公開する仮想の XML データ ソースで作業を行うされ、メモリ内の XML ドキュメントの特定の実装からメソッドが分離されるため、 `XNode`, 、`XmlReader`, 、または <xref:System.Xml.XPath.XPathNavigator>です。  
  
 **X のしないで** サブクラス `XmlDocument` を基になるオブジェクト モデルまたはデータ ソースの XML ビューを表す型を作成するかどうか。  
  
 *部分 © 2005年、2009 Microsoft Corporation します。 All rights reserved.*  
  
 *翔泳社からのアクセス許可によって検出 [Framework デザイン ガイドライン: 規則が、表現方法と再利用可能な .NET ライブラリを 2 nd Edition パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) は Cwalina Brad エイブラムスによる、Microsoft Windows の開発シリーズの一部として Addison\-wesley Professional、2008 年 10 月 22 日を公開します。*  
  
## 参照  
 [Framework デザイン ガイドライン](../../../docs/standard/design-guidelines/index.md)   
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)