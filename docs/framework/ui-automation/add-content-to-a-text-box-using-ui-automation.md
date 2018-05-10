---
title: UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- adding content to text boxes
- text boxes, adding content
- UI Automation, adding content to text boxes
ms.assetid: 8bdd1a73-1ecb-4a05-a891-a7827ebb767f
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 4b3179333119d1ff516c6176298fa25514a9ba66
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="add-content-to-a-text-box-using-ui-automation"></a>UI オートメーションを使用した、テキスト ボックスへのコンテンツの追加
> [!NOTE]
>  このドキュメントは、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] 名前空間で定義されているマネージ <xref:System.Windows.Automation> クラスを使用する .NET Framework 開発者を対象としています。 [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]の最新情報については、「 [Windows Automation API: UI Automation (Windows のオートメーション API: UI オートメーション)](http://go.microsoft.com/fwlink/?LinkID=156746)」を参照してください。  
  
 このトピックを使用する方法を示すコード例が含まれています。[!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)]単一行のテキスト ボックスにテキストを挿入します。 複数行およびリッチ テキスト コントロールを別の方法が提供される、[!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)]は適用されません。 例は、比較のための Win32 メソッドを使用して、同じ結果を達成する方法も示します。  
  
## <a name="example"></a>例  
 ターゲット アプリケーション内のテキスト コントロールのシーケンスで次の例の手順です。 各テキスト コントロールがかどうかをテストする<xref:System.Windows.Automation.ValuePattern>オブジェクトを取得するにを使用して、<xref:System.Windows.Automation.AutomationElement.TryGetCurrentPattern%2A>メソッドです。 場合は、テキスト コントロールはサポート<xref:System.Windows.Automation.ValuePattern>、<xref:System.Windows.Automation.ValuePattern.SetValue%2A>テキスト コントロールにユーザー定義の文字列を挿入するメソッドを使用します。 それ以外の場合、<xref:System.Windows.Forms.SendKeys.SendWait%2A?displayProperty=nameWithType>メソッドを使用します。  
  
 [!code-csharp[InsertText#InsertText](../../../samples/snippets/csharp/VS_Snippets_Wpf/InsertText/CSharp/Window1.xaml.cs#inserttext)]
 [!code-vb[InsertText#InsertText](../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InsertText/VisualBasic/Window1.xaml.vb#inserttext)]  
  
## <a name="see-also"></a>関連項目  
 [TextPattern の挿入テキスト サンプル](http://msdn.microsoft.com/library/67353f93-7ee2-42f2-ab76-5c078cf6ca16)
