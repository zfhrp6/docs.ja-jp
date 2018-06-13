---
title: Windows フォーム DataGridView コントロールでのデータの書式設定
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], formatting data
- data [Windows Forms], formatting in grids
- data grids [Windows Forms], formatting data
ms.assetid: 07bf558d-3748-42ba-8ba0-37fdef924081
ms.openlocfilehash: ae1947cf7c3825553837fa5f1ee288114988d28f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527775"
---
# <a name="data-formatting-in-the-windows-forms-datagridview-control"></a>Windows フォーム DataGridView コントロールでのデータの書式設定
<xref:System.Windows.Forms.DataGridView>コントロールがセルの値と、親列を表示するデータ型の間の自動変換を提供します。 テキスト ボックスの列はたとえば、日付、時刻、数、および列挙値の文字列形式を表示し、ユーザーが入力した文字列値をデータ ストアで必要な型に変換します。  
  
## <a name="formatting-with-the-datagridviewcellstyle-class"></a>DataGridViewCellStyle クラスを使用した書式設定  
 <xref:System.Windows.Forms.DataGridView>コントロールは、基本的なデータを使用してセル値の書式を提供、<xref:System.Windows.Forms.DataGridViewCellStyle>クラスです。 使用することができます、<xref:System.Windows.Forms.DataGridViewCellStyle.Format%2A>プロパティで説明されている書式指定子を使用して現在の既定のカルチャの形式の日付、時刻、数、および列挙の値を[型の書式設定](../../../../docs/standard/base-types/formatting-types.md)です。 これらの値を使用して特定のカルチャの書式を設定することもできます、<xref:System.Windows.Forms.DataGridViewCellStyle.FormatProvider%2A>プロパティです。 データを表示して、ユーザーが指定された形式で入力したデータの解析を指定された形式が使用されます。  
  
 <xref:System.Windows.Forms.DataGridViewCellStyle> Wordwrap、テキストの配置、およびデータベースの null 値のカスタム表示のクラスは追加の書式設定プロパティを提供します。 詳細については、「[方法 : Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)」を参照してください。  
  
## <a name="formatting-with-the-cellformatting-event"></a>書式設定のイベントに書式設定  
 基本的な書式設定がニーズを満たさない場合は、カスタム データのハンドラーで書式設定を指定できます、<xref:System.Windows.Forms.DataGridView.CellFormatting?displayProperty=nameWithType>イベント。 <xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs>ハンドラーに渡されるが、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>を最初に、セルの値を格納するプロパティです。 通常、この値は自動的に表示の種類に変換します。 値を自分で変換するには設定、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>プロパティの表示の種類の値。  
  
> [!NOTE]
>  変更をオーバーライドし、セルの書式指定文字列が有効な場合、<xref:System.Windows.Forms.ConvertEventArgs.Value%2A>プロパティ値を設定しない限り、<xref:System.Windows.Forms.DataGridViewCellFormattingEventArgs.FormattingApplied%2A>プロパティを`true`です。  
  
 <xref:System.Windows.Forms.DataGridView.CellFormatting>イベントを設定するときにも役立ちます<xref:System.Windows.Forms.DataGridViewCellStyle>個々 のセル プロパティの値に基づきます。 詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールでデータの書式をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)です。  
  
 ユーザー指定の値の既定の解析がニーズを満たさない場合は、処理、<xref:System.Windows.Forms.DataGridView.CellParsing>のイベント、<xref:System.Windows.Forms.DataGridView>カスタム解析を提供するコントロール。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Windows フォーム DataGridView コントロールでのデータの表示](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Windows フォーム DataGridView コントロールでのセルのスタイル](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのデータの書式を設定する](../../../../docs/framework/winforms/controls/how-to-format-data-in-the-windows-forms-datagridview-control.md)  
 [方法: Windows フォーム DataGridView コントロールのデータの書式設定をカスタマイズする](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)
