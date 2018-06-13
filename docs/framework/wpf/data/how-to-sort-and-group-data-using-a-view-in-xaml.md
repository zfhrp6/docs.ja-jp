---
title: '方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [WPF], grouping data in views in XAML
- XAML [WPF], sorting data in views
- grouping data in views in XAML [WPF]
- data binding [WPF], sorting data in views in XAML
- sorting data in views in XAML [WPF]
- XAML [WPF], grouping data in views
- views [WPF], sorting data
- views [WPF], grouping data
ms.assetid: 145c8c3f-dbdd-4d0d-816f-90b35eba7eda
ms.openlocfilehash: 80529420bcc5fdca473313e164b3d096732953f4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555831"
---
# <a name="how-to-sort-and-group-data-using-a-view-in-xaml"></a>方法 : XAML でビューを使用してデータの並べ替えおよびグループ化を行う
この例は、内のデータ コレクションのビューを作成する方法を示しています。[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 ビューを使用するグループ化、並べ替え、フィルター、の機能および現在のアイテムの概念です。  
  
## <a name="example"></a>例  
 次の例では、静的リソース名前*配置*のコレクションとして定義されて*場所*各内のオブジェクト*場所*オブジェクトは、市区町村名で構成されていましたし、状態です。 プレフィックス*src*名前空間にマップされているデータ ソース*場所*が定義されています。 プレフィックス*scm*にマップ`"clr-namespace:System.ComponentModel;assembly=WindowsBase"`と*dat*にマップ`"clr-namespace:System.Windows.Data;assembly=PresentationFramework"`です。  
  
 次の例では、市区町村名によって並べ替えられ、状態別にグループ化するデータ コレクションのビューを作成します。  
  
 [!code-xaml[CollectionViewSource#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#1)]  
  
 ビューは、次の例のように、バインディング ソースに指定できます。  
  
 [!code-xaml[CollectionViewSource#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#2)]  
  
 定義されている XML データへのバインドを<xref:System.Windows.Data.XmlDataProvider>リソースで XML 名の前に、@ 記号。  
  
 [!code-xaml[CollectionViewSource#XDPChunk](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#xdpchunk)]  
  
 [!code-xaml[CollectionViewSource#Attribute](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CollectionViewSource/CS/window1.xaml#attribute)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Data.CollectionViewSource>  
 [データ コレクションの既定のビューを取得する](../../../../docs/framework/wpf/data/how-to-get-the-default-view-of-a-data-collection.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
