---
title: '方法: システム フォント キーを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- resource keys [WPF], SystemFonts class
ms.assetid: 036ebea7-5677-4f60-8ba4-56c9f9d9b8bd
ms.openlocfilehash: c68f197daebd7423aa4ad2e7fdfb6e7f89c74ed0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544428"
---
# <a name="how-to-use-system-fonts-keys"></a>方法: システム フォント キーを使用する
システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。 <xref:System.Windows.SystemFonts> システム フォントの値と値へのバインドのシステム フォントのリソースの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemFonts.CaptionFontFamily%2A>と<xref:System.Windows.SystemFonts.CaptionFontFamilyKey%2A>です。  
  
 システム フォント メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。 アプリケーションの実行時にフォント メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的なリソースがあるキーワード*キー*プロパティ名に付加します。  
  
 次の例では、システム フォント動的リソースにアクセスして使用し、ボタンのスタイル設定またはカスタマイズを行う方法を示します。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例は、ボタンのスタイルを割り当てる<xref:System.Windows.SystemFonts>をボタンの値。  
  
## <a name="example"></a>例  
 [!code-xaml[SystemRes_snip#FontDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#fontdynamicresources)]  
  
## <a name="see-also"></a>関連項目  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemParameters を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)  
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)
