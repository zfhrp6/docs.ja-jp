---
title: '方法 : バインディングの更新の通知を設定する'
ms.date: 03/30/2017
helpviewer_keywords:
- notifications [WPF], binding updates
- data binding [WPF], notification of binding updates
- binding [WPF], updates [WPF], notifications of
ms.assetid: 5673073e-dbe1-49da-980a-484a88f9595a
ms.openlocfilehash: 896ce103361590dceecccf8534fd330aabe18086
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555842"
---
# <a name="how-to-set-up-notification-of-binding-updates"></a>方法 : バインディングの更新の通知を設定する
この例では、バインドのバインディング ターゲット (ターゲット) またはバインディング ソース (ソース) のプロパティが更新されたときに通知するように設定する方法を示します。  
  
## <a name="example"></a>例  
 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、バインドのソースまたはターゲットが更新されるたびにデータ更新イベントを発生させます。 内部的には、このイベントは、バインドされたデータが変更されているため、更新する必要があることを [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] に通知するために使用されます。 注するために、これらのイベントとも適切に機能する一方向または双方向をバインドするため、使用するデータ クラスを実装する必要があります、<xref:System.ComponentModel.INotifyPropertyChanged>インターフェイスです。 詳細については、「[プロパティの変更通知を実装する](../../../../docs/framework/wpf/data/how-to-implement-property-change-notification.md)」を参照してください。  
  
 設定、<xref:System.Windows.Data.Binding.NotifyOnTargetUpdated%2A>または<xref:System.Windows.Data.Binding.NotifyOnSourceUpdated%2A>プロパティ (またはその両方) に`true`のバインドにします。 このイベントをリッスンするために提供するハンドラーは、変更を通知する要素に直接アタッチするか、コンテキスト内の何かが変更されたことを認識する場合は、全体的なデータ コンテキストにアタッチする必要があります。  
  
 ターゲットのプロパティが更新されたときの通知を設定する方法の例を次に示します。  
  
 [!code-xaml[DirectionalBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml#2)]  
  
 その後、EventHandler\<T> デリゲート (この例では *OnTargetUpdated*) に基づいて、イベントを処理するハンドラーを割り当てることができます。  
  
 [!code-csharp[DirectionalBinding#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#3)]  
[!code-csharp[DirectionalBinding#EndEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DirectionalBinding/CSharp/Page1.xaml.cs#endevent)]  
  
 イベントのパラメーターを使用して、変更されたプロパティの詳細 (型や、複数の要素に同じハンドラーがアタッチされている場合の特定の要素など) を確認できます。これは、1 つの要素に複数のバインドされたプロパティがある場合に役に立つ可能性があります。  
  
## <a name="see-also"></a>関連項目  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
