---
title: '方法: 自動レイアウト用のグリッドを使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- grids [WPF], automatic layout
- automatic layout [WPF], grid use
ms.assetid: ab9de407-e0c1-4047-bdf0-24951bf73879
ms.openlocfilehash: 6ea0b64af07924867c2de97baf5a81f8e8da6a56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544623"
---
# <a name="how-to-use-a-grid-for-automatic-layout"></a>方法: 自動レイアウト用のグリッドを使用する
この例では、自動レイアウトの方法でグリッドを使用して、ローカライズ可能なアプリケーションを作成する方法について説明します。  
  
 ローカライズ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]時間のかかるプロセスを指定できます。 多くの場合、ローカライザーは、テキストの翻訳だけでなく、要素のサイズ変更や位置変更を行う必要もあります。 過去の各言語を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必要な調整が翻訳します。 機能を持つようになりました[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]調整の必要性が軽減される要素を設計することができます。 簡単に再サイズと位置を変更できるアプリケーションの作成方法と呼びます`auto layout`です。  
  
 次[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]ボタンとテキストの位置にグリッドを使用する例を示します。 セルの幅と高さに設定されている通知`Auto`; したがってイメージとボタンが含まれているセルが画像に合わせて調整します。 <xref:System.Windows.Controls.Grid>できると便利です、自動レイアウト アプローチ ローカライズ可能なアプリケーションを設計するときにそのコンテンツへの要素を調整できます。  
  
## <a name="example"></a>例  
 次の例では、グリッドを使用する方法を示します。  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 次の図は、コード サンプルの出力を示しています。  
  
 ![グリッドの例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
グリッド  
  
## <a name="see-also"></a>関連項目  
 [自動レイアウトの使用の概要](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [自動レイアウトを使用してボタンを作成する](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
