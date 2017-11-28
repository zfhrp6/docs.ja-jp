---
title: "方法 : プリンターを複製する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- print queues [WPF]
- cloning printers [WPF]
- printers [WPF], cloning
- print queues [WPF], cloning
- cloning print queues [WPF]
ms.assetid: dd6997c9-fe04-40f8-88a6-92e3ac0889eb
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 303cb9c1c5b6521839987a56cdc008eac0559cf1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-clone-a-printer"></a>方法 : プリンターを複製する
ほとんどの企業が、ある時点で、購入、同じモデルの複数のプリンターです。 通常、これらはすべてほぼ同一の構成の設定でインストールします。 各プリンターのインストールとできる時間がかかる場合、エラーが発生します。 <xref:System.Printing.IndexedProperties?displayProperty=nameWithType>名前空間および<xref:System.Printing.PrintServer.InstallPrintQueue%2A>で公開されているクラス[!INCLUDE[TLA#tla_avalonwinfx](../../../../includes/tlasharptla-avalonwinfx-md.md)]を即座に既存の印刷キューから任意の数の複製されたその他の印刷キューをインストールできるようになります。  
  
## <a name="example"></a>例  
 次の例では、2 番目の印刷キューは既存の印刷キューから複製されました。 最初の異なる 2 つ目の名前、場所、ポート、および共有状態でのみです。 これを行うための主な手順は次のとおりです。  
  
1.  作成、<xref:System.Printing.PrintQueue>を複製する予定の既存のプリンターのオブジェクト。  
  
2.  作成、<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>から、<xref:System.Printing.PrintSystemObject.PropertiesCollection%2A>の<xref:System.Printing.PrintQueue>です。 <xref:System.Collections.DictionaryEntry.Value%2A>このディクショナリ内の各エントリのプロパティから派生した型の 1 つのオブジェクトである<xref:System.Printing.IndexedProperties.PrintProperty>です。 これにはこのディクショナリ内のエントリの値を設定する 2 つの方法があります。  
  
    -   ディクショナリの使用**削除**と<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.Add%2A>エントリを削除してから再び、目的の値に追加する方法です。  
  
    -   ディクショナリの使用<xref:System.Printing.IndexedProperties.PrintPropertyDictionary.SetProperty%2A>メソッドです。  
  
     次の例では、両方の方法を示します。  
  
3.  作成、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> 「とき」に、その<xref:System.Printing.IndexedProperties.PrintBooleanProperty.Value%2A>に`true`。  
  
4.  使用して、<xref:System.Printing.IndexedProperties.PrintBooleanProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「とき」エントリです。  
  
5.  作成、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "ShareName"に、その<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>。  
  
6.  使用して、<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の"ShareName"エントリです。  
  
7.  新しいインスタンスを作成<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトし、設定、 <xref:System.Printing.IndexedProperties.PrintProperty.Name%2A> "Location"とその<xref:System.Printing.IndexedProperties.PrintStringProperty.Value%2A>に適切な<xref:System.String>します。  
  
8.  もう 1 つを使用して<xref:System.Printing.IndexedProperties.PrintStringProperty>オブジェクトの値を<xref:System.Printing.IndexedProperties.PrintPropertyDictionary>の「場所」のエントリ。  
  
9. 配列を作成する<xref:System.String>s。 各項目は、サーバー上のポートの名前です。  
  
10. 使用して<xref:System.Printing.PrintServer.InstallPrintQueue%2A>を新しい値で、新しいプリンターをインストールします。  
  
 例を下回っています。  
  
 [!code-csharp[ClonePrinter#ClonePrinter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClonePrinter/CSharp/Program.cs#cloneprinter)]
 [!code-vb[ClonePrinter#ClonePrinter](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClonePrinter/visualbasic/program.vb#cloneprinter)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Printing.IndexedProperties>  
 <xref:System.Printing.IndexedProperties.PrintPropertyDictionary>  
 <xref:System.Printing.LocalPrintServer>  
 <xref:System.Printing.PrintQueue>  
 <xref:System.Collections.DictionaryEntry>  
 [WPF のドキュメント](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [印刷の概要](../../../../docs/framework/wpf/advanced/printing-overview.md)
