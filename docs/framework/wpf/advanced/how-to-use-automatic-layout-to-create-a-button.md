---
title: '方法: 自動レイアウトを使用してボタンを作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- Button controls [WPF], creating with automatic layout
- automatic layout [WPF], creating buttons
ms.assetid: 96c206d0-9e77-4784-9d2d-5045aed2021c
ms.openlocfilehash: 34b372e886b31e801b5598da90299f9815c47620
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545215"
---
# <a name="how-to-use-automatic-layout-to-create-a-button"></a>方法: 自動レイアウトを使用してボタンを作成する
この例では、自動レイアウトの方法を使用して、ローカライズ可能なアプリケーションにボタンを作成する方法について説明します。  
  
 ローカライズ、[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]時間のかかるプロセスを指定できます。 多くの場合、ローカライザーは、テキストの翻訳だけでなく、要素のサイズ変更や位置変更を行う必要があります。 過去の各言語を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]必要な調整が翻訳します。 機能を持つようになりました[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]調整の必要性が軽減される要素を設計することができます。 簡単にサイズ変更や再配置できるアプリケーションの作成方法と呼びます`automatic layout`です。  
  
 次の 2 つ[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]の例は、ボタン以外の場合は英語のテキストとスペイン語のテキストのインスタンスを作成するアプリケーションを作成します。 テキストを除き、コードは同じであることに注目してください。ボタンがテキストに合わせて調整されます。  
  
## <a name="example"></a>例  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 次の図は、コード サンプルの出力を示しています。  
  
 ![同じテキストのボタンを異なる言語で](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
自動サイズ変更可能なボタン  
  
## <a name="see-also"></a>関連項目  
 [自動レイアウトの使用の概要](../../../../docs/framework/wpf/advanced/use-automatic-layout-overview.md)  
 [自動レイアウト用のグリッドを使用する](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
