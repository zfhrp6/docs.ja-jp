---
title: '方法 : FlowDocument の列区切り属性を使用する'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 678e01a35c286ea03f0385291d64f2f900f068c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543772"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>方法 : FlowDocument の列区切り属性を使用する
この例は、列区切りの機能を使用する方法を示します、<xref:System.Windows.Documents.FlowDocument>です。  
  
## <a name="example"></a>例  
 次の例では定義、 <xref:System.Windows.Documents.FlowDocument>、設定と、 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、 <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>属性。  <xref:System.Windows.Documents.FlowDocument>サンプルの内容の 1 つの段落が含まれています。  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 次の図は、の効果を示します、 <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>、 <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>、および<xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A>、レンダリングされた属性<xref:System.Windows.Documents.FlowDocument>です。  
  
 ![スクリーン ショット: FlowDocument Intra 列](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
