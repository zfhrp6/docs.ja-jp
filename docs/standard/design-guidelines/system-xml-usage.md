---
title: System.Xml の使用法
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology: dotnet-standard
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 82302f0d-a621-4c6f-b57d-999bd61f21a6
caps.latest.revision: 4
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 7e90dea873a007c9f148228a2566ff22d91185a3
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/18/2018
---
# <a name="systemxml-usage"></a><span data-ttu-id="93705-102">System.Xml の使用法</span><span class="sxs-lookup"><span data-stu-id="93705-102">System.Xml Usage</span></span>
<span data-ttu-id="93705-103">このセクションで内に存在するいくつかの型の使用方法について説明<xref:System.Xml?displayProperty=nameWithType>名前空間に XML データを表すために使用できます。</span><span class="sxs-lookup"><span data-stu-id="93705-103">This section talks about usage of several types residing in <xref:System.Xml?displayProperty=nameWithType> namespaces that can be used to represent XML data.</span></span>  
  
 <span data-ttu-id="93705-104">**X しないで**使用<xref:System.Xml.XmlNode>または<xref:System.Xml.XmlDocument>XML データを表します。</span><span class="sxs-lookup"><span data-stu-id="93705-104">**X DO NOT** use <xref:System.Xml.XmlNode> or <xref:System.Xml.XmlDocument> to represent XML data.</span></span> <span data-ttu-id="93705-105">インスタンスを使用して優先<xref:System.Xml.XPath.IXPathNavigable>、 <xref:System.Xml.XmlReader>、 <xref:System.Xml.XmlWriter>、またはのサブタイプ<xref:System.Xml.Linq.XNode>代わりにします。</span><span class="sxs-lookup"><span data-stu-id="93705-105">Favor using instances of <xref:System.Xml.XPath.IXPathNavigable>, <xref:System.Xml.XmlReader>, <xref:System.Xml.XmlWriter>, or subtypes of <xref:System.Xml.Linq.XNode> instead.</span></span> <span data-ttu-id="93705-106">`XmlNode` および`XmlDocument`パブリック Api で公開するために設計されていません。</span><span class="sxs-lookup"><span data-stu-id="93705-106">`XmlNode` and `XmlDocument` are not designed for exposing in public APIs.</span></span>  
  
 <span data-ttu-id="93705-107">**✓ しないで**使用`XmlReader`、 `IXPathNavigable`、またはのサブタイプ`XNode`をそのまま使用したり、XML を返すメンバーの入力または出力として。</span><span class="sxs-lookup"><span data-stu-id="93705-107">**✓ DO** use `XmlReader`, `IXPathNavigable`, or subtypes of `XNode` as input or output of members that accept or return XML.</span></span>  
  
 <span data-ttu-id="93705-108">代わりにこれらの抽象化を使用して`XmlDocument`、 `XmlNode`、または<xref:System.Xml.XPath.XPathDocument>仮想の XML データ ソースを公開する作業を行うされ、インメモリ XML ドキュメントの特定の実装からメソッドが分離されるため、 `XNode`、 `XmlReader`、または<xref:System.Xml.XPath.XPathNavigator>です。</span><span class="sxs-lookup"><span data-stu-id="93705-108">Use these abstractions instead of `XmlDocument`, `XmlNode`, or <xref:System.Xml.XPath.XPathDocument>, because this decouples the methods from specific implementations of an in-memory XML document and allows them to work with virtual XML data sources that expose `XNode`, `XmlReader`, or <xref:System.Xml.XPath.XPathNavigator>.</span></span>  
  
 <span data-ttu-id="93705-109">**X しないで**サブクラス`XmlDocument`を基になるオブジェクト モデルまたはデータ ソースの XML ビューを表す型を作成するかどうか。</span><span class="sxs-lookup"><span data-stu-id="93705-109">**X DO NOT** subclass `XmlDocument` if you want to create a type representing an XML view of an underlying object model or data source.</span></span>  
  
 <span data-ttu-id="93705-110">*部分 © 2005、2009 Microsoft Corporation します。All rights reserved.*</span><span class="sxs-lookup"><span data-stu-id="93705-110">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>  
  
 <span data-ttu-id="93705-111">*ピアソン教育, Inc. からのアクセス許可によって検出[Framework デザイン ガイドライン: 規則、表現方法、および再利用可能な .NET ライブラリを第 2 版パターン](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)は Cwalina と Brad Abrams、2008 年 10 月 22 日で発行されました。Microsoft Windows 開発シリーズの一部として、Addison-wesley Professional。*</span><span class="sxs-lookup"><span data-stu-id="93705-111">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93705-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="93705-112">See Also</span></span>  
 [<span data-ttu-id="93705-113">フレームワーク デザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="93705-113">Framework Design Guidelines</span></span>](../../../docs/standard/design-guidelines/index.md)  
 [<span data-ttu-id="93705-114">使用方法のガイドライン</span><span class="sxs-lookup"><span data-stu-id="93705-114">Usage Guidelines</span></span>](../../../docs/standard/design-guidelines/usage-guidelines.md)
