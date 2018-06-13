---
title: '方法 : クリップボードにデータを追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Clipboard [Windows Forms], copying data to
- data [Windows Forms], copying to Clipboard
ms.assetid: 25152454-0e78-40a9-8a9e-a2a5a274e517
ms.openlocfilehash: 6002acfadfd0e688ef432baacbdabffb83890cb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522068"
---
# <a name="how-to-add-data-to-the-clipboard"></a>方法 : クリップボードにデータを追加する
<xref:System.Windows.Forms.Clipboard>クラスは、Windows オペレーティング システムのクリップボード機能との対話に使用できるメソッドを提供します。 多くのアプリケーションでは、データの一時的なレポジトリとしてクリップボードを使用します。 たとえば、ワード プロセッサでは、カット アンド ペースト操作中に、クリップボードを使用します。 クリップボードも別の 1 つのアプリケーションからデータを転送するため便利です。  
  
 クリップボードにデータを追加するときは、他のアプリケーションは、その形式を使用する場合、データが認識できるように、データ形式を指定できます。 データを使用できるその他のアプリケーションの数を増やすには複数の異なる形式でクリップボードにデータを追加することもできます。  
  
 クリップボードの形式は、その形式を使用するアプリケーションが関連付けられているデータを取得できるようにする形式を識別する文字列です。 <xref:System.Windows.Forms.DataFormats>クラスは、使用できる定義済みの形式名を提供します。 独自の形式名を使用してもまたはオブジェクトの型の形式として使用できます。  
  
 1 つまたは複数の形式でクリップボードにデータを追加するには、使用、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>メソッドです。 このメソッドを任意のオブジェクトを渡すことができますが、複数の形式でデータを追加する必要があります最初に、データを追加する別のオブジェクトが複数の形式を使用するよう設計されています。 データを追加する通常、<xref:System.Windows.Forms.DataObject>を実装する任意の型を使用することができますが、<xref:System.Windows.Forms.IDataObject>インターフェイスです。  
  
 [!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]クリップボードの基本的な作業を容易に設計された新しいメソッドを使用して、クリップボードに直接データを追加することができます。 テキストなどの 1 つの一般的な形式でデータを操作する場合は、これらのメソッドを使用します。  
  
> [!NOTE]
>  すべての Windows ベースのアプリケーションでは、クリップボードを共有します。 そのため、別のアプリケーションに切り替えると、内容は変更されることがします。  
>   
>  <xref:System.Windows.Forms.Clipboard>クラスは、シングル スレッド アパートメント (STA) モードに設定のスレッドでのみ使用できます。 このクラスを使用することを確認、`Main`メソッドが付いて、<xref:System.STAThreadAttribute>属性。  
>   
>  オブジェクトをクリップボードに保存するのには、シリアル化可能にする必要があります。 型をシリアル化可能にするを使用してマークする、<xref:System.SerializableAttribute>属性。 クリップボードのメソッドにシリアル化できないオブジェクトを渡すと、例外をスローせず、メソッドは失敗します。 シリアル化の詳細については、「<xref:System.Runtime.Serialization>」を参照してください。  
  
### <a name="to-add-data-to-the-clipboard-in-a-single-common-format"></a>1 つの一般的な形式でクリップボードにデータを追加するには  
  
1.  使用して、 <xref:System.Windows.Forms.Clipboard.SetAudio%2A>、 <xref:System.Windows.Forms.Clipboard.SetFileDropList%2A>、 <xref:System.Windows.Forms.Clipboard.SetImage%2A>、または<xref:System.Windows.Forms.Clipboard.SetText%2A>メソッドです。 これらのメソッドはでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-add-data-to-the-clipboard-in-a-custom-format"></a>カスタム形式でクリップボードにデータを追加するには  
  
1.  使用して、<xref:System.Windows.Forms.Clipboard.SetData%2A>カスタム形式の名前を持つメソッドです。 このメソッドでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。  
  
     定義済みの形式名を使用することも、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッドです。 詳細については、「<xref:System.Windows.Forms.DataFormats>」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-add-data-to-the-clipboard-in-multiple-formats"></a>複数の形式でクリップボードにデータを追加するには  
  
1.  使用して、<xref:System.Windows.Forms.Clipboard.SetDataObject%2A>メソッドを渡します、<xref:System.Windows.Forms.DataObject>データを格納します。 このメソッドを使用してデータのバージョンでクリップボードを追加する必要がありますよりも前[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]です。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>関連項目  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [方法: クリップボードからデータを取得する](../../../../docs/framework/winforms/advanced/how-to-retrieve-data-from-the-clipboard.md)
