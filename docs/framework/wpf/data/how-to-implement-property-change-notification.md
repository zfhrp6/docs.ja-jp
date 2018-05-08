---
title: '方法 : プロパティの変更通知を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- notifications of change [WPF]
- data binding [WPF], property change notifications
- change notifications [WPF]
- properties [WPF], change notifications
ms.assetid: 30b59d9e-8c3a-4349-aa82-4be837e841cf
ms.openlocfilehash: a9c0fb433e2fa65e28db3b793e038b49f9d6353b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-property-change-notification"></a>方法 : プロパティの変更通知を実装する
サポートする<xref:System.Windows.Data.BindingMode.OneWay>または<xref:System.Windows.Data.BindingMode.TwoWay>を自動的に (たとえば、プレビュー ウィンドウをユーザーがフォームを編集するときに自動的に更新する)、バインディング ソースの動的な変更を反映するように、バインディング ターゲット プロパティを有効にするバインディング クラス適切なプロパティの変更通知を提供する必要があります。 この例を実装するクラスを作成する方法を示しています。<xref:System.ComponentModel.INotifyPropertyChanged>です。  
  
## <a name="example"></a>例  
 実装する<xref:System.ComponentModel.INotifyPropertyChanged>を宣言する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベントを作成し、`OnPropertyChanged`メソッドです。 次に、変更を通知する必要のある各プロパティについて、そのプロパティが更新されるたびに `OnPropertyChanged` を呼び出します。  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 方法の例を参照する`Person`クラスをサポートするために使用できます<xref:System.Windows.Data.BindingMode.TwoWay>バインドを参照してください[ ボックスにテキストが、ソースを更新するときに制御](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)です。  
  
## <a name="see-also"></a>関連項目  
 [バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
