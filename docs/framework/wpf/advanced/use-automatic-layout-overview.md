---
title: "自動レイアウトの使用の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 75066b59d0f3a686c66fdbdd187ba4c18e786e6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="use-automatic-layout-overview"></a>自動レイアウトの使用の概要
ここで作成する開発者向けのガイドラインを紹介[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]ローカライズ可能なアプリケーション[!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]です。 以前は、ローカライズされ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]が時間のかかるプロセスです。 各言語を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]ピクセル単位で調整を必須に合わせて変更されました。 適切な設計とコーディング標準では、今日[!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)]ローカライザーがあるサイズ変更や位置の変更を行うように構築できます。 簡単にサイズと位置を変更できるアプリケーションを作成する方法は、自動レイアウトが呼び出されを使用して実現できる[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションの設計。  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>自動レイアウトを使用する利点  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]プレゼンテーション システムは強力で柔軟なさまざまな言語の要件に合わせて調整できるアプリケーションの要素をレイアウトする機能を提供します。 次の一覧は、いくつかの自動レイアウトの利点を示しています。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]任意の言語にも表示されます。  
  
-   テキストを翻訳した後は、コントロールの位置とサイズを再調整する必要性が軽減されます。  
  
-   ウィンドウのサイズを再調整する必要性が軽減されます。  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]レイアウトは、任意の言語で正しく表示します。  
  
-   ローカライズは、文字列の翻訳より若干高であるポイントに削減できます。  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>自動レイアウトとコントロール  
 自動配置により、アプリケーションをコントロールのサイズを自動的に調整します。 たとえば、コントロールは、文字列の長さに合わせて変更できます。 この機能により、文字列を変換するローカライザー不要になった、翻訳されたテキストに合わせてコントロールのサイズを変更する必要があります。 次の例では、英語のコンテンツをボタンを作成します。  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 例では、スペイン語のボタンのために実行する必要がある、テキストを変更します。 たとえば、オブジェクトに適用された  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 次の図は、コード サンプルの出力を示しています。  
  
 ![同じテキストのボタンを異なる言語で](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
自動サイズ変更可能なボタン  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>自動レイアウトとコーディング標準  
 コーディングおよびデザインの標準と完全にローカライズできるを生成するルール セット自動レイアウト方法を使用する必要があります[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 次のガイドライン、自動レイアウト コーディングが容易になります。  
  
|コーディング規則|説明|  
|----------------------|-----------------|  
|絶対位置を使用しないでください。|-使用しない<xref:System.Windows.Controls.Canvas>ので絶対に要素を配置します。<br />-使用<xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.StackPanel>、および<xref:System.Windows.Controls.Grid>コントロールを配置します。<br />さまざまな種類のパネルの詳細についてを参照してください[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)です。|  
|ウィンドウの固定サイズを設定しません。|-使用<xref:System.Windows.Window.SizeToContent%2A>です。<br />-例。<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|<xref:System.Windows.FrameworkElement.FlowDirection%2A> を追加します。|<ul><li>追加、<xref:System.Windows.FrameworkElement.FlowDirection%2A>をアプリケーションのルート要素です。</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]双方向、および垂直方向のレイアウトを水平方向をサポートする便利な手段を提供します。 プレゼンテーション フレームワークで、<xref:System.Windows.FrameworkElement.FlowDirection%2A>レイアウトを定義するプロパティを使用できます。 フロー方向のパターンは次のとおりです。<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight>(LrTb)-ラテン、東アジア言語などの水平レイアウトです。</li><li><xref:System.Windows.FlowDirection.RightToLeft>(RlTb)-アラビア語やヘブライ語などの双方向です。</li></ul></li></ul>|  
|物理的なフォントではなく複合フォントを使用します。|<ul><li>複合のフォントを含む、<xref:System.Windows.Controls.Control.FontFamily%2A>プロパティはローカライズする必要はありません。</li><li>開発者では、次のフォントのいずれかを使用したり、独自に作成することができます。<br /><br /> <ul><li>グローバル ユーザー インターフェイス</li><li>グローバル San Serif</li><li>グローバル Serif</li></ul></li></ul>|  
|Xml:lang を追加します。|-追加、`xml:lang`ルート要素の属性、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]など`xml:lang="en-US"`英語版のアプリケーションにします。<br />のコンポジット フォントを使用するため`xml:lang`を使用するフォントを決定するには、多言語シナリオをサポートするには、このプロパティを設定します。|  
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>自動レイアウトとグリッド  
 <xref:System.Windows.Controls.Grid>要素は、自動レイアウト用に便利ですが、開発者は要素を配置を可能になります。 A<xref:System.Windows.Controls.Grid>コントロールは列と行の並べ替え方法を使用して、その子要素の間で使用可能な領域を配布できます。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素が複数のセルにまたがることができ、グリッド内にグリッドを設定することができます。 グリッドを作成し、複雑な配置することができるため便利です[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 次の例では、いくつかのボタンとテキストを配置するグリッドの使用方法を示します。 セルの幅と高さに設定されている通知<xref:System.Windows.GridUnitType.Auto>。 したがって、イメージとボタンが含まれているセルを画像に合わせて調整します。  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 次の図は、前のコードによって生成されるグリッドを示します。  
  
 ![グリッドの例](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
グリッド  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>自動レイアウトと IsSharedSizeScope プロパティを使用してグリッド  
 A<xref:System.Windows.Controls.Grid>要素はローカライズ可能なアプリケーションがコンテンツに合わせて調整コントロールを作成するに役立ちます。 ただし、時点たいコンテンツに関係なく特定のサイズを維持するためにコントロールできます。 たとえば、"OK"の場合は、「キャンセル」と可能性がありますしないようにするサイズをコンテンツに合わせてボタンのボタンを「参照」です。 この場合、<xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType>添付プロパティは複数の grid 要素間で同じサイズの変更を共有するために役立ちます。 次の例は、列と行の複数の間でデータをサイズ変更を共有する方法を示します<xref:System.Windows.Controls.Grid>要素。  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **注**完全なコード サンプルでは、次を参照してください[共有サイズ変更プロパティの間でグリッド。](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>参照  
 [WPF のグローバリゼーション](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [自動レイアウトを使用してボタンを作成する](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [自動レイアウト用のグリッドを使用する](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
