---
title: '方法 : XAML を使用してテーブルを定義する'
ms.date: 03/30/2017
helpviewer_keywords:
- XAML [WPF], defining tables
- documents [WPF], defining tables with XAML
- tables [WPF], defining with XAML
ms.assetid: 83f2dc58-437e-4cdc-b5dd-0019810c7a85
ms.openlocfilehash: 2a35a27567d962fc125cb3c408ccab95afa222af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543102"
---
# <a name="how-to-define-a-table-with-xaml"></a>方法 : XAML を使用してテーブルを定義する
次の例は、定義する方法を示します、<xref:System.Windows.Documents.Table>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。  このテーブルには 4 つの列 (によって表される<xref:System.Windows.Documents.TableColumn>要素) といくつかの行 (によって表される<xref:System.Windows.Documents.TableRow>要素) を含むデータもとしてタイトル、ヘッダーおよびフッター情報。  内の行を含める必要があります、<xref:System.Windows.Documents.TableRowGroup>要素。  テーブル内の各行は 1 つまたは複数のセルで構成されます (によって表される<xref:System.Windows.Documents.TableCell>要素)。  テーブル セル内のコンテンツに含まれる必要があります、<xref:System.Windows.Documents.Block>要素です。 ここでは<xref:System.Windows.Documents.Paragraph>要素が使用されます。  テーブルはハイパーリンクもホスト (によって表される、<xref:System.Windows.Documents.Hyperlink>要素) フッター行にします。  
  
## <a name="example"></a>例  
 [!code-xaml[TableSnippetsXAML#_TableXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TableSnippetsXAML/CS/Window1.xaml#_tablexaml)]  
  
 この例で定義されたテーブルのレンダリング結果を次の図に示します。  
  
 ![描画されたテーブル。](../../../../docs/framework/wpf/advanced/media/tableeg.png "TableEG")
