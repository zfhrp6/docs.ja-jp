---
title: "Serializing2 を中に空白の保持"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 93cfc1c14d75078170d6e1bbb3fc4ad72f47a206
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="preserving-white-space-while-serializing"></a>シリアル化時の空白の維持
このトピックでは、XML ツリーをシリアル化するときに空白を制御する方法について説明します。  
  
 一般的なシナリオでは、インデントされた XML を読み取り、メモリ内に空白のテキスト ノードなしで (つまり空白を維持せずに) XML ツリーを作成し、XML に対して何らかの操作を実行し、インデント付きで XML を保存します。 書式を設定して XML をシリアル化する場合は、XML ツリー内の有意の空白のみが維持されます。 これが [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] の既定の動作です。  
  
 もう 1 つのよくあるシナリオは、意図的にインデントされた XML を読み取って変更する場合です。 場合によっては、このインデントを一切変更しないようにする必要があります。 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] でこれを実現するには、XML を読み込む際または解析する際に空白を維持し、XML をシリアル化するときに書式設定を無効にします。  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>XML ツリーをシリアル化するメソッドの空白に関する動作  
 <xref:System.Xml.Linq.XElement> クラスと <xref:System.Xml.Linq.XDocument> クラスにある次のメソッドは、XML ツリーをシリアル化します。 XML ツリーは、ファイル、<xref:System.IO.TextReader>、または <xref:System.Xml.XmlReader> にシリアル化できます。 `ToString` メソッドは、文字列にシリアル化します。  
  
-   <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.ToString%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.ToString%2A?displayProperty=nameWithType>  
  
 メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取らない場合は、シリアル化された XML が書式設定 (インデント) されます。 この場合、XML ツリー内の意味のない空白はすべて破棄されます。  
  
 メソッドが <xref:System.Xml.Linq.SaveOptions> を引数として受け取る場合は、シリアル化された XML が書式設定 (インデント) されないことを指定できます。 この場合、XML ツリー内の空白はすべて維持されます。  
  
## <a name="see-also"></a>関連項目  
 [(Visual Basic) の XML ツリーをシリアル化します。](../../../../visual-basic/programming-guide/concepts/linq/serializing-xml-trees.md)
