---
title: "PrintForm コンポーネント (Visual Basic) |Microsoft ドキュメント"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: f0c51ef0131c874ed33af7a19f9145a790d14ade
ms.lasthandoff: 03/13/2017

---
# <a name="printform-component-visual-basic"></a>PrintForm コンポーネント (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントに対して[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]実行時に Windows フォームのイメージを印刷することができます</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。 この動作は、Visual Basic の以前のバージョンで使用されていた `PrintForm` メソッドの動作に代わるものです。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
## <a name="printform-component-overview"></a>PrintForm コンポーネントの概要  
 一般的に Windows フォームでは、紙の書類やレポートのような書式のフォームを作成して、フォームのイメージを印刷します。 使用できますが、<xref:System.Drawing.Printing.PrintDocument>コンポーネントには、多くのコードが必要になります</xref:System.Drawing.Printing.PrintDocument>。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントでは、プリンター、印刷プレビュー ウィンドウ、またはファイルの形式のイメージを使用せずに印刷することができます、<xref:System.Drawing.Printing.PrintDocument>コンポーネント</xref:System.Drawing.Printing.PrintDocument></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントが上にある、 **Visual Basic power Packs**のタブ、**ツールボックス**</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。 これをフォームまでドラッグすると、コンポーネント トレイ (フォーム底部の下の小さな領域) に表示されます。 このコンポーネントを選択した場合、その動作を定義するプロパティを **[プロパティ]** ウィンドウで設定できます。 これらすべてのプロパティは、コードで設定することもできます。 インスタンスを作成することも、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>デザイン時コンポーネントを追加せずにコード内のコンポーネント</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
 フォームの印刷時には、フォームのクライアント領域にあるものすべてが印刷されます。 これには、すべてのコントロール、およびグラフィックス メソッドを使ってフォームに描画されたすべてのテキストやグラフィックスも含まれます。 既定では、フォームのタイトル バー、スクロール バー、境界は印刷されません。 既定でも、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントは、フォームの表示部分のみを出力します</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。 たとえば、ユーザーが実行時にフォームのサイズを変更した場合、現在表示されているコントロールとグラフィックスだけが印刷されます。  
  
 使用される既定のプリンター、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントは、オペレーティング システムのコントロール パネルの設定によって決まります</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
 印刷が開始された後、標準的な<xref:System.Drawing.Printing.PrintDocument>印刷ダイアログ ボックスが表示されます</xref:System.Drawing.Printing.PrintDocument>。 このダイアログ ボックスで、ユーザーは印刷ジョブを取り消すことができます。  
  
### <a name="key-methods-properties-and-events"></a>主要なメソッド、プロパティ、およびイベント  
 重要なメソッド、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントは、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>メソッドで、プリンター、印刷プレビュー ウィンドウ、またはファイルへのフォームのイメージを印刷します</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。 2 つのバージョンがある、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>メソッド:</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
  
-   パラメーターなしの基本的なバージョン:`Print()`  
  
-   印刷動作を指定するパラメーターを持つオーバー ロードされたバージョン:`Print(printForm As Form, printFormOption As PrintOption)`  
  
     オーバーロードされたメソッドの `PrintOption` パラメーターは、フォーム印刷の基礎となる実装を指定し、フォームのタイトル バー、スクロール バー、境界を印刷するかどうか、またフォーム内のスクロール可能部分を印刷するかどうかを決定します。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>プロパティは、キー プロパティ、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネント</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>。 このプロパティは、出力をプリンターに送るか、印刷プレビュー ウィンドウに表示するか、またはカプセル化された PostScript ファイルとして保存するかを決定します。 場合、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>にプロパティが設定されている<xref:System.Drawing.Printing.PrintAction>、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A>プロパティ パスとファイル名を指定します</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A></xref:System.Drawing.Printing.PrintAction></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A>プロパティは、基になる<xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>オブジェクトを使用するプリンターおよび印刷するコピーの数などの設定を指定することができます</xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A>へのアクセスを提供します。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> さらに、プリンターの機能 (色や両面印刷のサポートなど) を問い合わせることもできます。 このプロパティは **[プロパティ]** ウィンドウには表示されず、コードを介してのみアクセスできます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>を起動するときに印刷するフォームを指定するプロパティを使用、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネント プログラムを使用しています</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A>。 デザイン時にこのコンポーネントをフォームに追加した場合、そのフォームが既定になります。  
  
 キーのイベントを<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネントには、次が含まれます:</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint>イベントです。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> 発生したときに、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>メソッドが呼び出されるとドキュメント印刷の最初のページの前に</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint>イベントです。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> 最後のページが印刷された後で発生します。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings>イベントです。</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> 各ページが印刷される直前に発生します。  
  
### <a name="remarks"></a>コメント  
 フォームにテキストが含まれている場合、またはグラフィックスによって描画される<xref:System.Drawing.Graphics>メソッド、基本的なを使用して<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>(`Print()`) メソッドをそれを印刷して</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:System.Drawing.Graphics> グラフィックスが一部のオペレーティング システム上にレンダリングされない場合があるときに、オーバー ロードされた<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>メソッドを使用します</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>。  
  
 フォームの幅がプリンター用紙の幅より広い場合、フォームの右側が途切れる可能性があります。 印刷用のフォームをデザインするときには、標準的な用紙サイズにフォームが収まることを確認してください。  
  
## <a name="example"></a>例  
 次の例の一般的な使用方法を示しています、<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>コンポーネント</xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm>。  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>   
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A></xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>   
 [方法: PrintForm コンポーネントを使用してフォームを印刷します。](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)   
 [方法: フォームのクライアント領域を印刷](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)   
 [方法: クライアントと、フォームの非クライアント領域を印刷](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)   
 [方法: スクロール可能フォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
