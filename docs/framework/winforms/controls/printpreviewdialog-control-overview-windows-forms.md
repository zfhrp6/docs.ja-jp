---
title: PrintPreviewDialog コントロールの概要 (Windows フォーム)
ms.date: 01/08/2018
f1_keywords:
- PrintPreviewDialog
helpviewer_keywords:
- PrintPreviewDialog control (using designer), about PrintPreviewDialog
ms.assetid: efd4ee8d-6edd-47ec-88e4-4a4759bd2384
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0946220017fb78775f045bb225d84ea95aecd06b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33538338"
---
# <a name="printpreviewdialog-control-overview-windows-forms"></a>PrintPreviewDialog コントロールの概要 (Windows フォーム)
Windows フォーム<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは、構成済みのダイアログ ボックスを表示するために使用する方法、 [PrintDocument](../../../../docs/framework/winforms/controls/printdocument-component-windows-forms.md)印刷したときに表示されます。 独自のダイアログ ボックスではなく簡易ソリューションとして、Windows ベースのアプリケーションの中で使用します。 このコントロールには、印刷を開始するボタン、ズーム イン用のボタン、1 ページまたは複数ページを表示するボタン、およびダイアログ ボックスを閉じるためのボタンが含まれています。  
  
## <a name="key-properties-and-methods"></a>キー プロパティとメソッド  
 コントロールのキー プロパティは<xref:System.Windows.Forms.PrintPreviewDialog.Document%2A>、プレビューするドキュメントを設定します。 ドキュメントがある必要があります、<xref:System.Drawing.Printing.PrintDocument>オブジェクト。 ダイアログ ボックスを表示するために呼び出す必要があります、<xref:System.Windows.Forms.Form.ShowDialog%2A>メソッドです。 アンチ エイリアスが滑らかにテキストを行うことができます。 が、低速です。 表示することもできます。これを使用する設定、<xref:System.Windows.Forms.PrintPreviewDialog.UseAntiAlias%2A>プロパティを`true`です。  
  
 特定のプロパティは、<xref:System.Windows.Forms.PrintPreviewControl>を<xref:System.Windows.Forms.PrintPreviewDialog>が含まれています。 (これを追加する必要はありません<xref:System.Windows.Forms.PrintPreviewControl>フォームに含まれている自動的に、<xref:System.Windows.Forms.PrintPreviewDialog>をフォームにダイアログ ボックスを追加するとします)。を通じて使用可能なプロパティの例については、<xref:System.Windows.Forms.PrintPreviewControl>は、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>と<xref:System.Windows.Forms.PrintPreviewControl.Rows%2A>プロパティで、コントロールの水平方向および垂直方向に表示されているページの数を決定します。 アクセスすることができます、<xref:System.Windows.Forms.PrintPreviewControl.Columns%2A>プロパティとして`PrintPreviewDialog1.PrintPreviewControl.Columns`Visual basic で`printPreviewDialog1.PrintPreviewControl.Columns`Visual c# の場合、または`printPreviewDialog1->PrintPreviewControl->Columns`で[!INCLUDE[vcprvc](../../../../includes/vcprvc-md.md)]です。  
  
## <a name="printpreviewdialog-performance"></a>PrintPreviewDialog パフォーマンス

次の条件下で、<xref:System.Windows.Forms.PrintPreviewDialog>コントロールが非常に遅いを初期化します。

- ネットワーク プリンターが使用されます。
- 双方向の設定など、このプリンターに関するユーザー設定が変更されます。
  
アプリの .NET Framework 4.5.2 で実行されている場合に、次のキーを追加することができます、 \<appSettings > のパフォーマンスを向上させるために、構成ファイルのセクション<xref:System.Windows.Forms.PrintPreviewDialog>の初期化を制御します。

```xml
<appSettings>
   <add key="EnablePrintPreviewOptimization" value="true" />
</appSettings>
```
場合、`EnablePrintPreviewOptimization`キーが、他の値に設定されているか、キーが存在しない場合、最適化は適用されません。

アプリの .NET Framework 4.6 またはそれ以降のバージョンで実行されている場合に、次のスイッチを追加することができます、 [ \<AppContextSwitchOverrides >](../../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)内の要素、 [\<ランタイム >](../../configure-apps/file-schema/runtime/index.md)アプリ構成ファイルのセクションの内容:

```xml
<runtime >
   <!-- AppContextSwitchOverrides values are in the form of 'key1=true|false;key2=true|false -->
   <AppContextSwitchOverrides value = "Switch.System.Drawing.Printing.OptimizePrintPreview=true" />
</runtime >
``` 
スイッチが存在しない場合、またはその他の値に設定されている場合は、最適化は適用されません。 

使用する場合、<xref:System.Drawing.Printing.PrintDocument.QueryPageSettings>のパフォーマンスのプリンターの設定を変更するイベント、<xref:System.Windows.Forms.PrintPreviewDialog>コントロールは、最適化の構成スイッチが設定されている場合でもは改善されません。  

## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.PrintPreviewDialog>  
 [PrintPreviewControl コントロールの概要](../../../../docs/framework/winforms/controls/printpreviewcontrol-control-overview-windows-forms.md)  
 [PrintPreviewDialog コントロール](../../../../docs/framework/winforms/controls/printpreviewdialog-control-windows-forms.md)  
 [ダイアログ ボックス コントロールおよびコンポーネント](../../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)
