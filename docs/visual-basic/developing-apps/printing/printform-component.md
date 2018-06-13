---
title: PrintForm コンポーネント (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- PrintForm component [Visual Basic]
ms.assetid: 03de98b8-b54c-4764-91d7-83c64e974750
ms.openlocfilehash: 6cb7cfe022b2b4d23f47a47ec70f08d5c0ccbc7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33591409"
---
# <a name="printform-component-visual-basic"></a>PrintForm コンポーネント (Visual Basic)
<xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> Visual basic のコンポーネントでは、実行時に Windows フォームのイメージを印刷することができます。 この動作は、Visual Basic の以前のバージョンで使用されていた `PrintForm` メソッドの動作に代わるものです。  
  
 PowerPack コントロールは、Visual Studio には含まれなくなりましたが、 [ダウンロード センター](http://www.microsoft.com/en-us/download/details.aspx?id=25169)からダウンロードできます。  
  
## <a name="printform-component-overview"></a>PrintForm コンポーネントの概要  
 一般的に Windows フォームでは、紙の書類やレポートのような書式のフォームを作成して、フォームのイメージを印刷します。 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使ってこれを行うこともできますが、これを使用すると多くのコードが必要になる可能性があります。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントを使用すると、 <xref:System.Drawing.Printing.PrintDocument> コンポーネントを使わなくても、フォームのイメージをプリンターに印刷し、印刷プレビュー ウィンドウに表示し、ファイルに出力することができます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントは、 **[ツールボックス]** の **[Visual Basic PowerPacks]** タブにあります。 これをフォームまでドラッグすると、コンポーネント トレイ (フォーム底部の境界下の小さな領域) に表示されます。 このコンポーネントを選択した場合、その動作を定義するプロパティを **[プロパティ]** ウィンドウで設定できます。 これらすべてのプロパティは、コードで設定することもできます。 さらに、デザイン時にコンポーネントを追加する代わりに、コードで <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントのインスタンスを作成することもできます。  
  
 フォームの印刷時には、フォームのクライアント領域にあるものすべてが印刷されます。 これには、すべてのコントロール、およびグラフィックス メソッドを使ってフォームに描画されたすべてのテキストやグラフィックスも含まれます。 既定では、フォームのタイトル バー、スクロール バー、境界は印刷されません。 また既定では、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントはフォーム内の表示されている部分だけを印刷します。 たとえば、ユーザーが実行時にフォームのサイズを変更した場合、現在表示されているコントロールとグラフィックスだけが印刷されます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントが使用する既定のプリンターは、オペレーティング システムのコントロール パネルの設定によって決まります。  
  
 印刷が始まると、標準の <xref:System.Drawing.Printing.PrintDocument> 印刷ダイアログ ボックスが表示されます。 このダイアログ ボックスで、ユーザーは印刷ジョブを取り消すことができます。  
  
### <a name="key-methods-properties-and-events"></a>主要なメソッド、プロパティ、およびイベント  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントの主要なメソッドは、フォームのイメージをプリンター、印刷プレビュー ウィンドウ、またはファイルに出力する <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> メソッドです。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> メソッドには、次の 2 つの形式があります。  
  
-   パラメーターなしの基本形式: `Print()`  
  
-   印刷動作を指定するパラメーターを使用する、オーバーロードされた形式: `Print(printForm As Form, printFormOption As PrintOption)`  
  
     オーバーロードされたメソッドの `PrintOption` パラメーターは、フォーム印刷の基礎となる実装を指定し、フォームのタイトル バー、スクロール バー、境界を印刷するかどうか、またフォーム内のスクロール可能部分を印刷するかどうかを決定します。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティは、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントの主要なプロパティです。 このプロパティは、出力をプリンターに送るか、印刷プレビュー ウィンドウに表示するか、またはカプセル化された PostScript ファイルとして保存するかを決定します。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A> プロパティを <xref:System.Drawing.Printing.PrintAction.PrintToFile>に設定した場合、パスとファイル名が <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintFileName%2A> プロパティによって指定されます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrinterSettings%2A> プロパティは、基礎となる <xref:System.Drawing.Printing.PrintDocument.PrinterSettings%2A> オブジェクトへのアクセスを提供します。このオブジェクトで、使用するプリンターや印刷部数などを設定できます。 さらに、プリンターの機能 (色や両面印刷のサポートなど) を問い合わせることもできます。 このプロパティは **[プロパティ]** ウィンドウには表示されず、コードを介してのみアクセスできます。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Form%2A> プロパティは、 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントをプログラム的に呼び出すときに、どのフォームを印刷するかを指定します。 デザイン時にこのコンポーネントをフォームに追加した場合、そのフォームが既定になります。  
  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントの主要なイベントは、次のとおりです。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.BeginPrint> イベント。 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> メソッドが呼び出されたとき (ドキュメントの最初のページが印刷される前) に発生します。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.EndPrint> イベント。 最後のページが印刷された後で発生します。  
  
-   <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.QueryPageSettings> イベント。 各ページが印刷される直前に発生します。  
  
### <a name="remarks"></a>コメント  
 <xref:System.Drawing.Graphics> メソッドによって描画されたテキストやグラフィックスがフォームに含まれる場合、これを印刷するには基本的な <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> (`Print()`) メソッドを使用してください。 オーバーロードされた <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A> メソッドを使用すると、オペレーティング システムによってはグラフィックスが描画されない場合があります。  
  
 フォームの幅がプリンター用紙の幅より広い場合、フォームの右側が途切れる可能性があります。 印刷用のフォームをデザインするときには、標準的な用紙サイズにフォームが収まることを確認してください。  
  
## <a name="example"></a>例  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm> コンポーネントの一般的な使用例を次に示します。  
  
```  
' Visual Basic.  
Dim pf As New PrintForm  
pf.Form = Me  
pf.PrintAction = PrintToPrinter  
pf.Print()  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.Print%2A>  
 <xref:Microsoft.VisualBasic.PowerPacks.Printing.PrintForm.PrintAction%2A>  
 [方法: PrintForm コンポーネントを使用してフォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-form-by-using-the-printform-component.md)  
 [方法: フォームのクライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-the-client-area-of-a-form.md)  
 [方法: フォームのクライアント領域と非クライアント領域を印刷する](../../../visual-basic/developing-apps/printing/how-to-print-client-and-non-client-areas-of-a-form.md)  
 [方法: スクロール可能フォームを印刷する](../../../visual-basic/developing-apps/printing/how-to-print-a-scrollable-form.md)
