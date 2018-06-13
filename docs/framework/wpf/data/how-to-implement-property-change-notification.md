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
ms.locfileid: "33555991"
---
# <a name="how-to-implement-property-change-notification"></a><span data-ttu-id="083b0-102">方法 : プロパティの変更通知を実装する</span><span class="sxs-lookup"><span data-stu-id="083b0-102">How to: Implement Property Change Notification</span></span>
<span data-ttu-id="083b0-103">サポートする<xref:System.Windows.Data.BindingMode.OneWay>または<xref:System.Windows.Data.BindingMode.TwoWay>を自動的に (たとえば、プレビュー ウィンドウをユーザーがフォームを編集するときに自動的に更新する)、バインディング ソースの動的な変更を反映するように、バインディング ターゲット プロパティを有効にするバインディング クラス適切なプロパティの変更通知を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="083b0-103">To support <xref:System.Windows.Data.BindingMode.OneWay> or <xref:System.Windows.Data.BindingMode.TwoWay> binding to enable your binding target properties to automatically reflect the dynamic changes of the binding source (for example, to have the preview pane updated automatically when the user edits a form), your class needs to provide the proper property changed notifications.</span></span> <span data-ttu-id="083b0-104">この例を実装するクラスを作成する方法を示しています。<xref:System.ComponentModel.INotifyPropertyChanged>です。</span><span class="sxs-lookup"><span data-stu-id="083b0-104">This example shows how to create a class that implements <xref:System.ComponentModel.INotifyPropertyChanged>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="083b0-105">例</span><span class="sxs-lookup"><span data-stu-id="083b0-105">Example</span></span>  
 <span data-ttu-id="083b0-106">実装する<xref:System.ComponentModel.INotifyPropertyChanged>を宣言する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>イベントを作成し、`OnPropertyChanged`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="083b0-106">To implement <xref:System.ComponentModel.INotifyPropertyChanged> you need to declare the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> event and create the `OnPropertyChanged` method.</span></span> <span data-ttu-id="083b0-107">次に、変更を通知する必要のある各プロパティについて、そのプロパティが更新されるたびに `OnPropertyChanged` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="083b0-107">Then for each property you want change notifications for, you call `OnPropertyChanged` whenever the property is updated.</span></span>  
  
 [!code-csharp[SimpleBinding#PersonClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Person.cs#personclass)]
 [!code-vb[SimpleBinding#PersonClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Person.vb#personclass)]  
  
 <span data-ttu-id="083b0-108">方法の例を参照する`Person`クラスをサポートするために使用できます<xref:System.Windows.Data.BindingMode.TwoWay>バインドを参照してください[ ボックスにテキストが、ソースを更新するときに制御](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md)です。</span><span class="sxs-lookup"><span data-stu-id="083b0-108">To see an example of how the `Person` class can be used to support <xref:System.Windows.Data.BindingMode.TwoWay> binding, see [Control When the TextBox Text Updates the Source](../../../../docs/framework/wpf/data/how-to-control-when-the-textbox-text-updates-the-source.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="083b0-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="083b0-109">See Also</span></span>  
 [<span data-ttu-id="083b0-110">バインディング ソースの概要</span><span class="sxs-lookup"><span data-stu-id="083b0-110">Binding Sources Overview</span></span>](../../../../docs/framework/wpf/data/binding-sources-overview.md)  
 [<span data-ttu-id="083b0-111">データ バインディングの概要</span><span class="sxs-lookup"><span data-stu-id="083b0-111">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="083b0-112">方法トピック</span><span class="sxs-lookup"><span data-stu-id="083b0-112">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
