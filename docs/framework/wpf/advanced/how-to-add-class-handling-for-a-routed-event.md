---
title: '方法 : ルーティング イベントのクラス処理を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- routed events [WPF], class handlers
- task_core_add_class_handling_routed_properties [WPF]
- class handlers [WPF], routed events
ms.assetid: 15b7b06c-9112-4ee5-b30a-65d10c5c5df6
ms.openlocfilehash: 85c3491c9035d807b4c654659a8641121bb5709f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33545364"
---
# <a name="how-to-add-class-handling-for-a-routed-event"></a>方法 : ルーティング イベントのクラス処理を追加する
クラス ハンドラーまたはルート内の特定のノード上のインスタンス ハンドラーによって、ルーティングされたイベントを処理できます。 クラス ハンドラーは、最初に、呼び出され、インスタンス処理からイベントを抑制するか、基本クラスによって所有されているイベントに関するその他のイベント固有の動作を紹介するクラスの実装で使用できます。 この例では、クラス ハンドラーを実装するための 2 つの密接に関連する手法を示します。  
  
## <a name="example"></a>例  
 この例に基づくカスタム クラスを使用して、<xref:System.Windows.Controls.Canvas>パネルです。 アプリケーションの基本的な前提は、カスタムのクラスがインターセプトし、いずれかのマウスの左ボタンをクリックして、子要素のクラスやそれにインスタンス ハンドラーが呼び出される前に、その処理をマークすることを含め、子要素にビヘイビアーを導入することです。  
  
 <xref:System.Windows.UIElement>クラスをクラスに処理を有効にする仮想メソッドを公開する、<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>単にイベントをオーバーライドして、イベント。 これは、このような仮想メソッドがクラスの階層のどこかに利用可能な場合は、クラス処理を実装する最も簡単な方法です。 次のコードは、 <xref:System.Windows.UIElement.OnPreviewMouseLeftButtonDown%2A> "MyEditContainer"から派生する実装<xref:System.Windows.Controls.Canvas>です。 実装では、イベント引数を処理済みとして示し、基本的な表示の変更を元の要素に与えるコードを追加します。  
  
 [!code-csharp[ClassHandling#OnStarClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#onstarclasshandler)]
 [!code-vb[ClassHandling#OnStarClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#onstarclasshandler)]  
  
 ユーティリティ メソッドを使用して直接クラス処理を追加できる場合はなく仮想基底クラスまたはその特定のメソッドの使用可能な、<xref:System.Windows.EventManager>クラス、<xref:System.Windows.EventManager.RegisterClassHandler%2A>です。 このメソッドは、クラス処理を追加しているクラスの静的な初期化内でのみ呼び出す必要があります。 この例の別のハンドラーを追加する<xref:System.Windows.UIElement.PreviewMouseLeftButtonDown>、ここでは、登録されているクラスは、カスタム クラスとします。 これに対し、仮想メソッドを使用する場合、登録されているクラスは、実際に、<xref:System.Windows.UIElement>基本クラスです。 基底クラスとサブクラスのクラス処理を登録する場所の場合、サブクラス ハンドラーは、最初に呼び出されます。 最初、このハンドラーは、メッセージ ボックスを表示すると、仮想メソッドのハンドラーで視覚的変更し、表示される、アプリケーションで動作になります。  
  
 [!code-csharp[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ClassHandling/CSharp/SDKSampleLibrary/class1.cs#staticandregisterclasshandler)]
 [!code-vb[ClassHandling#StaticAndRegisterClassHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ClassHandling/visualbasic/sdksamplelibrary/class1.vb#staticandregisterclasshandler)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.EventManager>  
 [ルーティング イベントの処理済みとしてのマーキング、およびクラス処理](../../../../docs/framework/wpf/advanced/marking-routed-events-as-handled-and-class-handling.md)  
 [ルーティング イベントを処理する](../../../../docs/framework/wpf/advanced/how-to-handle-a-routed-event.md)  
 [ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)
