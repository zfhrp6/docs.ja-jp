---
title: '方法: SystemParameters を使用する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], SystemParameters
ms.assetid: 02e7a5de-94eb-4953-b91c-52e6c872ad5b
ms.openlocfilehash: 07b73d78a022e508f9ed8ca2e80b71bc2ab89910
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544636"
---
# <a name="how-to-use-systemparameters"></a>方法: SystemParameters を使用する
この例は、アクセスしのプロパティを使用する方法を示しています。<xref:System.Windows.SystemParameters>スタイルまたはボタンをカスタマイズするためにします。  
  
## <a name="example"></a>例  
 システム リソースは、システム設定と一貫性のあるビジュアルを作成できるようにするために、いくつかのシステムに基づく設定をリソースとして公開します。 <xref:System.Windows.SystemParameters> システム パラメーターの値のプロパティと値へのバインドのリソース キーの両方を含むクラスです。 たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>は、<xref:System.Windows.SystemParameters>プロパティの値と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>は、対応するリソース キー。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]のメンバーを使用することができます<xref:System.Windows.SystemParameters>静的プロパティの使用状況、または (キーとして静的プロパティの値) の動的リソース参照のいずれかとして。 アプリケーションの実行時にシステムに基づく値を自動的に更新する場合は、動的リソース参照を使用します。それ以外の場合は、静的参照を使用します。 リソース キーは、サフィックスを持ちます`Key`プロパティ名に付加します。  
  
 次の例は、アクセスおよびの静的な値を使用する方法を示しています。<xref:System.Windows.SystemParameters>スタイルを設定したり、ボタンをカスタマイズします。 このマークアップの例を適用して、ボタンのサイズを<xref:System.Windows.SystemParameters>をボタンの値。  
  
 [!code-xaml[SystemRes_snip#ParameterStaticResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml#parameterstaticresources)]  
  
 値を使用する<xref:System.Windows.SystemParameters>コードでは、静的参照または動的リソース参照を使用する必要はありません。 代わりの値を使用して、<xref:System.Windows.SystemParameters>クラスです。 静的なプロパティの実行時の動作として定義されていますキー以外のプロパティが明らか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ように、システムによってホストされているがリアルタイムでプロパティを再評価され、ユーザーによる値の変更システム アカウントでは適切です。 次の例を使用してボタンの高さと幅を設定する方法を示します<xref:System.Windows.SystemParameters>値。  
  
 [!code-csharp[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/Pane1.xaml.cs#parameterresourcescode)]
 [!code-vb[SystemRes_snip#ParameterResourcesCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SystemRes_snip/VisualBasic/Pane1.xaml.vb#parameterresourcescode)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.SystemParameters>  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [システム パラメーター キーを使用する](../../../../docs/framework/wpf/advanced/how-to-use-system-parameters-keys.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/resources-how-to-topics.md)
