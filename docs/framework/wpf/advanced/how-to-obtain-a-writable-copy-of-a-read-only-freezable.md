---
title: '方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cloning Freezable objects [WPF]
- Freezable objects [WPF], modifiable clones
ms.assetid: d028de61-bbe9-4d62-b656-8fe3b1b2ca24
ms.openlocfilehash: 894a2e42ca3f5cbb159c3129227f4b03e71fc4ee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543622"
---
# <a name="how-to-obtain-a-writable-copy-of-a-read-only-freezable"></a>方法 : 読み取り専用の Freezable の書き込み可能なコピーを取得する
この例を使用する方法を示しています、<xref:System.Windows.Freezable.Clone%2A>読み取り専用の書き込み可能なコピーを作成するメソッド<xref:System.Windows.Freezable>です。  
  
 後に、<xref:System.Windows.Freezable>オブジェクトがマークされている読み取り専用 ("凍結"した)、として、それを変更できません。 ただし、使用することができます、<xref:System.Windows.Freezable.Clone%2A>固定されたオブジェクトの変更可能な複製を作成します。  
  
## <a name="example"></a>例  
 次の例は、固定の変更可能な複製を作成<xref:System.Windows.Media.SolidColorBrush>オブジェクト。  
  
 [!code-csharp[freezablesample_procedural#CloneExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/freezablesample_procedural/CSharp/freezablesample.cs#cloneexample)]
 [!code-vb[freezablesample_procedural#CloneExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/freezablesample_procedural/visualbasic/freezablesample.vb#cloneexample)]  
  
 詳細については<xref:System.Windows.Freezable>、オブジェクトを参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Freezable>  
 <xref:System.Windows.Freezable.CloneCurrentValue%2A>  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/advanced/base-elements-how-to-topics.md)
