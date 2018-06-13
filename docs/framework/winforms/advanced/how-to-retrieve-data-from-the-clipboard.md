---
title: '方法 : クリップボードからデータを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- pasting Clipboard data
- Clipboard [Windows Forms], retrieving data
ms.assetid: 99612537-2c8a-449f-aab5-2b3b28d656e7
ms.openlocfilehash: e06fb509bed32df0c18f2a03ae89765b3334b2c8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33524080"
---
# <a name="how-to-retrieve-data-from-the-clipboard"></a>方法 : クリップボードからデータを取得する
<xref:System.Windows.Forms.Clipboard>クラスは、Windows オペレーティング システムのクリップボード機能との対話に使用できるメソッドを提供します。 多くのアプリケーションでは、データの一時的なレポジトリとしてクリップボードを使用します。 たとえば、ワード プロセッサでは、カット アンド ペースト操作中に、クリップボードを使用します。 クリップボードも別の 1 つのアプリケーションから情報を転送するため便利です。  
  
 一部のアプリケーションでは、データを使用できる可能性のあるその他のアプリケーションの数を増やすに複数の形式でクリップボードにデータを保存します。 クリップボードの形式は、形式を識別する文字列です。 識別された形式を使用するアプリケーションでは、クリップボードに関連付けられているデータを取得できます。 <xref:System.Windows.Forms.DataFormats>クラスは、使用できる定義済みの形式名を提供します。 独自の形式名を使用したり、オブジェクトの型の形式として使用できます。 クリップボードにデータを追加する方法の詳細については、次を参照してください。[する方法: クリップボードのデータの追加](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)です。  
  
 を、クリップボードに特定の形式でデータが含まれているかどうかを判断するには、のいずれかを使用、 `Contains`*形式*メソッドまたは<xref:System.Windows.Forms.Clipboard.GetData%2A>メソッドです。 クリップボードからデータを取得するには、いずれかを使用、 `Get`*形式*メソッドまたは<xref:System.Windows.Forms.Clipboard.GetData%2A>メソッドです。 これらのメソッドはで新しく[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]です。  
  
 バージョンを使用して、クリップボードからデータにアクセスするよりも前[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]を使用して、<xref:System.Windows.Forms.Clipboard.GetDataObject%2A>メソッドの返されたメソッドを呼び出すと<xref:System.Windows.Forms.IDataObject>です。 たとえば、呼び出す特定の形式が、返されたオブジェクトで使用できるかどうかを判断するのには<xref:System.Windows.Forms.IDataObject.GetDataPresent%2A>メソッドです。  
  
> [!NOTE]
>  すべての Windows ベースのアプリケーションでは、システム クリップボードを共有します。 そのため、別のアプリケーションに切り替えると、内容は変更されることがします。  
>   
>  <xref:System.Windows.Forms.Clipboard>クラスは、シングル スレッド アパートメント (STA) モードに設定のスレッドでのみ使用できます。 このクラスを使用することを確認、`Main`メソッドが付いて、<xref:System.STAThreadAttribute>属性。  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-single-common-format"></a>1 つの一般的な形式でクリップボードからデータを取得するには  
  
1.  使用して、 <xref:System.Windows.Forms.Clipboard.GetAudioStream%2A>、 <xref:System.Windows.Forms.Clipboard.GetFileDropList%2A>、 <xref:System.Windows.Forms.Clipboard.GetImage%2A>、または<xref:System.Windows.Forms.Clipboard.GetText%2A>メソッドです。 必要に応じて、使用して、対応する`Contains`*形式*データが特定の形式で使用できるかどうかを決定するには、最初のメソッドです。 これらのメソッドはでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#2)]
     [!code-vb[System.Windows.Forms.Clipboard#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#2)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-a-custom-format"></a>カスタム形式でクリップボードからデータを取得するには  
  
1.  使用して、<xref:System.Windows.Forms.Clipboard.GetData%2A>カスタム形式の名前を持つメソッドです。 このメソッドでのみ使用可能な[!INCLUDE[dnprdnext](../../../../includes/dnprdnext-md.md)]します。  
  
     定義済みの形式名を使用することも、<xref:System.Windows.Forms.Clipboard.SetData%2A>メソッドです。 詳細については、「<xref:System.Windows.Forms.DataFormats>」を参照してください。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#3)]
     [!code-vb[System.Windows.Forms.Clipboard#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#3)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
### <a name="to-retrieve-data-from-the-clipboard-in-multiple-formats"></a>複数の形式でクリップボードからデータを取得するには  
  
1.  <xref:System.Windows.Forms.Clipboard.GetDataObject%2A> メソッドを使用します。 このメソッドを使用のバージョンでクリップボードからデータを取得する必要がありますよりも前[!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)]です。  
  
     [!code-csharp[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.Clipboard#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#4)]  
    [!code-csharp[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/CS/form1.cs#100)]
    [!code-vb[System.Windows.Forms.Clipboard#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.Clipboard/vb/form1.vb#100)]  
  
## <a name="see-also"></a>関連項目  
 [ドラッグ アンド ドロップ操作とクリップボードのサポート](../../../../docs/framework/winforms/advanced/drag-and-drop-operations-and-clipboard-support.md)  
 [方法: クリップボードにデータを追加する](../../../../docs/framework/winforms/advanced/how-to-add-data-to-the-clipboard.md)
