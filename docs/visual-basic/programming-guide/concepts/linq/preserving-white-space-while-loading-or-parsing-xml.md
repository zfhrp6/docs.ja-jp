---
title: "読み込みまたは XML2 を解析中に空白の維持 |Microsoft ドキュメント"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 39e4270acc0e9a9df5c3855f8c087f41d9612197
ms.lasthandoff: 03/13/2017

---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>XML の読み込み時または解析時の空白の維持
このトピックでは、空白に対する [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の動作を制御する方法について説明します。  
  
 一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] の既定の動作です。  
  
 もう&1; つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。  
  
 このトピックでは、空白に対する、XML ツリーを設定するメソッドの動作について説明します。 XML ツリーをシリアル化する場合は、空白を制御する方法の詳細については、次を参照してください。[維持空白中にシリアル化する](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md)です。  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>XML ツリーを設定するメソッドの動作  
 以下の方法で、<xref:System.Xml.Linq.XElement>と<xref:System.Xml.Linq.XDocument>クラスは、XML ツリーを設定します</xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XElement>。 ファイルから XML ツリーを設定することができます、 <xref:System.IO.TextReader>、 <xref:System.Xml.XmlReader>、または文字列:</xref:System.Xml.XmlReader> </xref:System.IO.TextReader>  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=fullName>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName></xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=fullName>  
  
 メソッドを取らない場合<xref:System.Xml.Linq.LoadOptions>を引数としては維持されません余分な空白</xref:System.Xml.Linq.LoadOptions>。  
  
 ほとんどの場合、メソッドを取る場合<xref:System.Xml.Linq.LoadOptions>を引数として必要に応じてとして維持できます余分な空白、XML ツリー内のテキスト ノード</xref:System.Xml.Linq.LoadOptions>。 ただし、このメソッドがから XML を読み込んでいる場合、 <xref:System.Xml.XmlReader>、<xref:System.Xml.XmlReader>空白を維持するかどうかを決定します</xref:System.Xml.XmlReader></xref:System.Xml.XmlReader>。 設定<xref:System.Xml.Linq.LoadOptions>効果はありません</xref:System.Xml.Linq.LoadOptions>。  
  
 これらのメソッドでは、空白を維持すると場合、意味のない空白が挿入として XML ツリーに<xref:System.Xml.Linq.XText>ノード</xref:System.Xml.Linq.XText>。 空白が維持されない場合、テキスト ノードは挿入されません。  
  
 <xref:System.Xml.XmlWriter>。</xref:System.Xml.XmlWriter>を使用して XML ツリーを作成することができます。 書き込まれたノード、<xref:System.Xml.XmlWriter>がツリーに挿入されます</xref:System.Xml.XmlWriter>。 ただし、このメソッドを使用して XML ツリーを構築すると、ノードが空白かどうかにかかわらず、また空白に意味があるかどうかにかかわらず、すべてのノードが維持されます。  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) の XML の解析](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)
