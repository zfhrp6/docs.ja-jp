---
title: "System.Xml の使用法"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a9bfa0f984f97e774d00a64fc3fd8489b3d5b40e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemxml-usage"></a>System.Xml の使用法
このセクションで内に存在するいくつかの型の使用方法について説明<xref:System.Xml?displayProperty=nameWithType>名前空間に XML データを表すために使用できます。  
  
 **X しないで**使用<xref:System.Xml.XmlNode>または<xref:System.Xml.XmlDocument>XML データを表します。 インスタンスを使用して優先<xref:System.Xml.XPath.IXPathNavigable>、 <xref:System.Xml.XmlReader>、 <xref:System.Xml.XmlWriter>、またはのサブタイプ<xref:System.Xml.Linq.XNode>代わりにします。 `XmlNode`および`XmlDocument`パブリック Api で公開するために設計されていません。  
  
 **✓ しないで**使用`XmlReader`、 `IXPathNavigable`、またはのサブタイプ`XNode`をそのまま使用したり、XML を返すメンバーの入力または出力として。  
  
 代わりにこれらの抽象化を使用して`XmlDocument`、 `XmlNode`、または<xref:System.Xml.XPath.XPathDocument>仮想の XML データ ソースを公開する作業を行うされ、インメモリ XML ドキュメントの特定の実装からメソッドが分離されるため、 `XNode`、 `XmlReader`、または<xref:System.Xml.XPath.XPathNavigator>です。  
  
 **X しないで**サブクラス`XmlDocument`を基になるオブジェクト モデルまたはデータ ソースの XML ビューを表す型を作成するかどうか。  
  
 *部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*  
  
 *ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*  
  
## <a name="see-also"></a>関連項目  
 [フレームワーク デザインのガイドライン](../../../docs/standard/design-guidelines/index.md)  
 [使用方法のガイドライン](../../../docs/standard/design-guidelines/usage-guidelines.md)
