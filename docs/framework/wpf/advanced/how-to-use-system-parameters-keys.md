---
title: "方法: システム パラメーター キーを使用する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- resource keys [WPF], SystemParameters class
- classes [WPF], SystemParameters
ms.assetid: 77571283-d16c-45bb-9f69-cafbbf72b21e
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b5f45f386c58b0577a2716c6fe1396f4c44f4ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-system-parameters-keys"></a>方法: システム パラメーター キーを使用する
システム リソースは、開発者がシステム設定と一貫性のあるビジュアルを作成できるようにするために、多くのシステム メトリックをリソースとして公開します。 <xref:System.Windows.SystemParameters>システム パラメーターの値と値へのバインドのリソース キーの両方を含むクラスは、— たとえば、<xref:System.Windows.SystemParameters.FullPrimaryScreenHeight%2A>と<xref:System.Windows.SystemParameters.FullPrimaryScreenHeightKey%2A>です。 システム パラメーター メトリックは、静的なリソースとしても、動的なリソースとしても使用できます。 アプリケーションの実行時にパラメーター メトリックを自動的に更新する場合は、動的リソースを使用します。それ以外の場合は、静的リソースを使用します。  
  
> [!NOTE]
>  動的なリソースがあるキーワード*キー*プロパティ名に付加します。  
  
 次の例では、ボタンのスタイル設定やカスタマイズを行うために、システム パラメーター動的リソースにアクセスして使用する方法を示します。 これは、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]例を割り当てることで、ボタンのサイズを<xref:System.Windows.SystemParameters>ボタンの幅と高さの値。  
  
## <a name="example"></a>例  
 [!code-xaml[SystemRes_snip#ParameterDynamicResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SystemRes_snip/CSharp/MyApp.xaml#parameterdynamicresources)]  
  
## <a name="see-also"></a>関連項目  
 [システム ブラシで領域を塗りつぶす](../../../../docs/framework/wpf/graphics-multimedia/how-to-paint-an-area-with-a-system-brush.md)  
 [SystemFonts を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemfonts.md)  
 [SystemParameters を使用する](../../../../docs/framework/wpf/advanced/how-to-use-systemparameters.md)
