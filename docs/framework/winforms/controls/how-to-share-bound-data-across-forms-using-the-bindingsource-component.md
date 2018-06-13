---
title: '方法 : BindingSource コンポーネントを使用してフォーム間でバインド データを共有する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: a0c68372301d984fc388f37a5ce798cbf99d802b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33536593"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>方法 : BindingSource コンポーネントを使用してフォーム間でバインド データを共有する
<xref:System.Windows.Forms.BindingSource> コンポーネントを使用してフォーム間でデータを簡単に共有できます。 たとえば、データ ソースのデータを集計する 1 つの読み取り専用のフォームと、データ ソース内の現在選択されているアイテムについての詳細情報を含む別の編集可能なフォームを表示することがあります。 この例は、このシナリオを示しています。  
  
## <a name="example"></a>例  
 次のコード例は、<xref:System.Windows.Forms.BindingSource> およびフォーム間でバインドされたデータを共有する方法を示しています。 この例で、共有された <xref:System.Windows.Forms.BindingSource> が子フォームのコンストラクターに渡されます。 子フォームでは、メイン フォームで現在選択されているアイテムのデータをユーザーが編集することができます。  
  
> [!NOTE]
>  例の <xref:System.Windows.Forms.BindingSource> コンポーネントの <xref:System.Windows.Forms.BindingSource.BindingComplete> イベントは、2 つの形式が同期を保つために処理されます。 これを実行する理由の詳細については、「[方法: 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)」を参照してください。  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>コードのコンパイル  
 この例で必要な要素は次のとおりです。  
  
-   System、System.Windows.Forms、System.Drawing、System.Data、および System.Xml アセンブリへの参照。  
  
 コマンドラインからこの例を Visual Basic または Visual c# のビルドについては、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。 この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。  また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。  
  
## <a name="see-also"></a>関連項目  
 [BindingSource コンポーネント](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Windows フォームでのデータ バインディング](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [方法: データ バインドで発生するエラーと例外を処理する](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
