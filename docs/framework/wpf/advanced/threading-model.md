---
title: スレッド モデル
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text on buttons [WPF], updating
- message processing [WPF], nested
- blocking operations [WPF]
- Common Language Runtime (CLR), locking mechanism
- locking mechanism of Common Language Runtime (CLR)
- threading model [WPF]
- Word [WPF], spelling checking
- button text [WPF], updating
- spelling checking in Word [WPF]
- asynchronous behavior [WPF], exposing
- nested message processing [WPF]
- reentrancy [WPF]
ms.assetid: 02d8fd00-8d7c-4604-874c-58e40786770b
ms.openlocfilehash: 15115cc0ed14cb5605100ebe47abd5cd4dc02ec0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549504"
---
# <a name="threading-model"></a>スレッド モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] スレッド処理の問題の開発者を保存する設計されています。 その結果、ほとんどの[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]開発者は、複数のスレッドを使用するインターフェイスを記述する必要はありません。 マルチ スレッド プログラムは複雑でデバッグが困難であるため、避けてシングル スレッドが存在する場合。  
  
 関係なくどの程度設計上、ただし、いいえ[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]フレームワークができるソリューションを提供する、シングル スレッドの問題のすべての種類。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 閉じるは、複数のスレッドを向上させるような状況はまだあります[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]の応答性またはアプリケーションのパフォーマンスです。 いくつかの背景情報の資料を紹介した後は、このペーパーは、これらの状況について説明し、最後にいくつかの低レベルの詳細の詳細についてはします。  
  

  
> [!NOTE]
>  このトピックでは、スレッドを使用して、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>非同期呼び出しのメソッドです。 呼び出しての非同期呼び出しを行うことも、<xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>メソッドで、実行、<xref:System.Action>または<xref:System.Func%601>をパラメーターとして。  <xref:System.Windows.Threading.Dispatcher.InvokeAsync%2A>メソッドを返します、<xref:System.Windows.Threading.DispatcherOperation>または<xref:System.Windows.Threading.DispatcherOperation%601>を持つ、<xref:System.Windows.Threading.DispatcherOperation.Task%2A>プロパティです。 使用することができます、`await`いずれかのキーワード、<xref:System.Windows.Threading.DispatcherOperation>または関連付けられた<xref:System.Threading.Tasks.Task>です。 <xref:System.Threading.Tasks.Task> または <xref:System.Windows.Threading.DispatcherOperation> によって返される <xref:System.Windows.Threading.DispatcherOperation%601> を同期的に待機する必要がある場合、<xref:System.Windows.Threading.TaskExtensions.DispatcherOperationWait%2A> 拡張メソッドを呼び出します。  呼び出す<xref:System.Threading.Tasks.Task.Wait%2A?displayProperty=nameWithType>デッドロックが発生します。 使用しての詳細については、<xref:System.Threading.Tasks.Task>非同期操作を実行するタスクの並列化を参照してください。  <xref:System.Windows.Threading.Dispatcher.Invoke%2A>メソッドにも使用するオーバー ロードが、<xref:System.Action>または<xref:System.Func%601>をパラメーターとして。  使用することができます、<xref:System.Windows.Threading.Dispatcher.Invoke%2A>をデリゲートに渡すことで同期させるメソッドを呼び出す<xref:System.Action>または<xref:System.Func%601>です。  
  
<a name="threading_overview"></a>   
## <a name="overview-and-the-dispatcher"></a>概要、およびディスパッチャー  
 通常、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが 2 つのスレッドの開始: 表示および管理用に別の処理の 1 つ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 レンダリング スレッドが効率的に実行中にバック グラウンドで非表示、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの入力を受け取り、イベントを処理、画面の描画およびアプリケーション コードを実行します。 ほとんどのアプリケーションが 1 つを使用して[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが、状況によってがいくつかの使用を推奨します。 について説明しますこの例を使用して後で。  
  
 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのキューの作業と呼ばれるオブジェクト内の項目、<xref:System.Windows.Threading.Dispatcher>です。 <xref:System.Windows.Threading.Dispatcher> は作業項目を優先順位に従って選択し、それぞれを最後まで実行します。  すべて[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドは少なくとも 1 つである必要があります<xref:System.Windows.Threading.Dispatcher>、および各<xref:System.Windows.Threading.Dispatcher>正確に 1 つのスレッドでの作業項目を実行することができます。  
  
 最大化する応答性の高い、使いやすいアプリケーションを構築することが重要、<xref:System.Windows.Threading.Dispatcher>小さな作業項目を保持することでスループットです。 により、この項目は達しませんにとどまっている古い、<xref:System.Windows.Threading.Dispatcher>キュー処理を待機しています。 入力と応答の間に遅延ユーザーはストレスを感じることができます。  
  
 方法、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーション大規模な操作を処理する必要がありますか。 場合、コードを使用するか、大量の計算では、または、いくつかのリモート サーバー上のデータベースのクエリを実行する必要がありますか。 まま、別のスレッドで大規模な操作を処理する、応答が通常は、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]内の項目に傾向が空きスレッド、<xref:System.Windows.Threading.Dispatcher>キュー。 大規模な操作が完了したら、その結果を報告できるに戻す、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]のスレッドを表示します。  
  
 従来、[!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)]により[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]は作成元のスレッドのみがアクセスする要素。 つまりが完了すると、いくつか実行時間の長いタスクを担当するバック グラウンド スレッドにテキスト ボックスを更新できません。 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] これは、整合性を確保ため[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]コンポーネントです。 リスト ボックスでしたにくい描画中に、バック グラウンド スレッドによってその内容が更新された場合。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] この調整を適用する組み込みの相互排他メカニズムがあります。 ほとんどのクラス[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から派生<xref:System.Windows.Threading.DispatcherObject>です。 構築時に、<xref:System.Windows.Threading.DispatcherObject>への参照を格納、<xref:System.Windows.Threading.Dispatcher>現在実行中のスレッドにリンクします。 実際には、<xref:System.Windows.Threading.DispatcherObject>それを作成したスレッドを関連付けます。 プログラムの実行中、<xref:System.Windows.Threading.DispatcherObject>そのパブリックを呼び出すことができます<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>メソッドです。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 調べ、 <xref:System.Windows.Threading.Dispatcher> 、現在のスレッドに関連付けられているし、比較する、<xref:System.Windows.Threading.Dispatcher>構築中に格納されている参照します。 一致しない場合は、<xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A>例外をスローします。 <xref:System.Windows.Threading.DispatcherObject.VerifyAccess%2A> 属するすべてのメソッドの開始時に呼び出されるものでは、<xref:System.Windows.Threading.DispatcherObject>です。  
  
 1 つのスレッドを変更できるだけの場合、 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]、方法はバック グラウンド スレッドと対話するユーザーですか? バック グラウンド スレッドを求めることができます、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの代理で操作を実行します。 これは、含む作業項目を登録することで、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 <xref:System.Windows.Threading.Dispatcher>クラスは作業項目を登録するための 2 つのメソッドを提供します。<xref:System.Windows.Threading.Dispatcher.Invoke%2A>と<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>です。 どちらの方法では、デリゲートの実行をスケジュールします。 <xref:System.Windows.Threading.Dispatcher.Invoke%2A> – の同期呼び出しは、つまりまで返されません、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが実際にはデリゲートの実行を終了します。 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 非同期と直ちに返されます。  
  
 <xref:System.Windows.Threading.Dispatcher>優先順位によって、キューに、要素を並べ替えます。 要素を追加するときに指定できる 10 のレベルがある、<xref:System.Windows.Threading.Dispatcher>キュー。 これらの優先順位はで保持されます、<xref:System.Windows.Threading.DispatcherPriority>列挙します。 に関する詳細情報<xref:System.Windows.Threading.DispatcherPriority>レベルは含まれて、[!INCLUDE[TLA2#tla_winfxsdk](../../../../includes/tla2sharptla-winfxsdk-md.md)]ドキュメント。  
  
<a name="samples"></a>   
## <a name="threads-in-action-the-samples"></a>スレッドの動作: サンプル  
  
<a name="prime_number"></a>   
### <a name="a-single-threaded-application-with-a-long-running-calculation"></a>実行時間の長い計算でシングル スレッド アプリケーション  
 ほとんど[!INCLUDE[TLA#tla_gui#plural](../../../../includes/tlasharptla-guisharpplural-md.md)]大部分のユーザーの操作への応答で生成されるイベントの待機中にアイドル状態の時間を費やしています。 慎重なプログラミング アイドル時間する建設的に使用できますの応答性に影響を与えず、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]で行われている操作を中断する入力を許可しないスレッド モデル、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 つまりに戻るにことを確認する必要があります、<xref:System.Windows.Threading.Dispatcher>古い前に、入力イベントの保留中の処理を定期的にします。  
  
 次に例を示します。  
  
 ![含まれる素数のスクリーン ショット](../../../../docs/framework/wpf/advanced/media/threadingprimenumberscreenshot.PNG "ThreadingPrimeNumberScreenShot")  
  
 この単純なアプリケーションは、素数を検索して 3 から上方にカウントします。 ユーザーがクリックしたとき、**開始**ボタン、検索を開始します。 プログラムでは、素数を検出すると、その探索でユーザー インターフェイスを更新します。 任意の時点では、ユーザーは、検索を停止できます。  
  
 単純なのでが素数の検索が永続的ないくつかの問題を提示に進んでください。  ボタンの click イベント ハンドラー内で検索全体を処理した場合は与えられません、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドが他のイベントを処理します。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]入力やプロセスに対応できないというメッセージです。 再描画し、ボタンのクリックに応答しません。  
  
 個別のスレッドでの素数の検索を実施してでしたが、同期の問題に対処する必要がありますが、します。 シングル スレッドのアプローチで直接更新することが検出された最大の素数を一覧表示するラベル。  
  
 管理しやすいチャンクに計算のタスクを中断して定期的に戻ることが、<xref:System.Windows.Threading.Dispatcher>およびイベントを処理します。 紹介[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を再描画して、入力を処理することです。  
  
 計算とイベント処理の間での処理時間を分割する最善の方法はから計算を管理する、<xref:System.Windows.Threading.Dispatcher>です。 使用して、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>メソッド内の素数のチェックをスケジュールお同じキューを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]からイベントが描画されます。 この例では、一度に 1 つの素数のチェックのみをスケジュールします。 素数のチェックが完了したら、すぐに次のチェックをスケジュールします。 このチェックが保留にした場合のみ進みます[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]イベントが処理されました。  
  
 ![ディスパッチャー キューの図](../../../../docs/framework/wpf/advanced/media/threadingdispatcherqueue.PNG "ThreadingDispatcherQueue")  
  
 [!INCLUDE[TLA#tla_word](../../../../includes/tlasharptla-word-md.md)] スペル チェックこのメカニズムを使用して実現しています。 スペル チェックのアイドル時間を使用して、バック グラウンドで行われますが、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 コードを見てをみましょう。  
  
 次の例では、ユーザー インターフェイスを作成する XAML を示します。  
  
 [!code-xaml[ThreadingPrimeNumbers#ThreadingPrimeNumberXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml#threadingprimenumberxaml)]  
  
 次の例では、分離コードを示します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumbercodebehind)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumbercodebehind)]  
  
 次の例では、対応するイベント ハンドラー、<xref:System.Windows.Controls.Button>です。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberstartorstop)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberStartOrStop](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberstartorstop)]  
  
 テキストの更新だけでなく、<xref:System.Windows.Controls.Button>の最初の素数のチェックをスケジュール設定するデリゲートを追加することで、このハンドラーは、<xref:System.Windows.Threading.Dispatcher>キュー。 このイベント ハンドラーには、作業が完了した後、<xref:System.Windows.Threading.Dispatcher>このデリゲートの実行を選択します。  
  
 既に説明したよう、<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>は、<xref:System.Windows.Threading.Dispatcher>メンバー デリゲートの実行をスケジュールするために使用します。 この場合、ユーザーが選択、<xref:System.Windows.Threading.DispatcherPriority.SystemIdle>優先度。 <xref:System.Windows.Threading.Dispatcher>を処理する重要なイベントがない場合にのみ、このデリゲートは実行されます。 [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] 応答性がチェックの番号よりも重要です。 番号のチェックのルーチンを表す新しいデリゲートを渡します。  
  
 [!code-csharp[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingPrimeNumbers/CSharp/Window1.xaml.cs#threadingprimenumberchecknextnumber)]
 [!code-vb[ThreadingPrimeNumbers#ThreadingPrimeNumberCheckNextNumber](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingPrimeNumbers/visualbasic/mainwindow.xaml.vb#threadingprimenumberchecknextnumber)]  
  
 このメソッドは、次の数が奇数の素数を確認します。 メソッドが直接更新の主要なである場合、 `bigPrime` <xref:System.Windows.Controls.TextBlock>探索を反映するようにします。 これは、計算は、コンポーネントの作成に使用された同じスレッドで発生しているため実行できます。 計算に使用する別のスレッド、選択したより複雑な同期機構を使用し、更新プログラムを実行する必要が、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 このような状況は、次について説明します。  
  
 このサンプルの完全なソース コードについては、[実行時間の長い計算のサンプルを使用して、シングル スレッド アプリケーション](http://go.microsoft.com/fwlink/?LinkID=160038)  
  
<a name="weather_sim"></a>   
### <a name="handling-a-blocking-operation-with-a-background-thread"></a>バック グラウンド スレッドでブロック操作の処理  
 グラフィカル アプリケーションでのブロック操作の処理は難しくなります。 アプリケーションが停止したように表示されるので、イベント ハンドラーからブロッキング メソッドを呼び出すしたくありません。 別のスレッドを使用してこれらの操作を処理が完了したら、おと同期するために、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの直接変更できないため、[!INCLUDE[TLA2#tla_gui](../../../../includes/tla2sharptla-gui-md.md)]ワーカー スレッドからです。 使用して<xref:System.Windows.Threading.Dispatcher.Invoke%2A>または<xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A>にデリゲートを挿入する、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 最終的に、これらのデリゲートを変更する権限を持つ実行は[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]要素。  
  
 この例では、天気予報を取得するリモート プロシージャ コールを模倣します。 この呼び出しを実行する個別のワーカー スレッドを使用し、スケジュールで更新メソッド、<xref:System.Windows.Threading.Dispatcher>の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドの完了時にします。  
  
 ![UI スクリーン ショットを気象条件](../../../../docs/framework/wpf/advanced/media/threadingweatheruiscreenshot.PNG "ThreadingWeatherUIScreenShot")  
  
 [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweathercodebehind)]
 [!code-vb[ThreadingWeatherForecast#ThreadingWeatherCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweathercodebehind)]  
  
 記録する詳細情報の一部を次に示します。  
  
-   ボタンのハンドラーを作成します。  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherbuttonhandler)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherButtonHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherbuttonhandler)]  
  
 ボタンをクリックすると、お時計の図が表示され、それをアニメーション化を開始します。 ここには、ボタンが無効にします。 呼び出すお、`FetchWeatherFromServer`メソッドで新しいスレッドとし、戻り値を許可する、<xref:System.Windows.Threading.Dispatcher>天気予報を収集するを待つためにイベントを処理します。  
  
-   天気の取得  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherfetchweather)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherFetchWeather](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherfetchweather)]  
  
 煩雑にならないように、この例ではネットワーク用のコードでは、実際がありません。 代わりに、4 秒間スリープ状態に新しいスレッドを配置することでネットワーク アクセスの遅延をシミュレートします。 このとき、元の[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドがまだ実行されていると、イベントに応答しています。 アニメーションの実行と、最小化残す、このメッセージを表示し、最大化するには、ボタンも引き続き機能します。  
  
 報告する時間の遅延が完了したら、際、天気予報をランダムに選択したことには、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 この作業を行うへの呼び出しをスケジュールすることによって`UpdateUserInterface`で、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドのスレッドを使用して<xref:System.Windows.Threading.Dispatcher>です。 このスケジュールされたメソッドの呼び出しを天気を説明する文字列を渡します。  
  
-   更新します [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]  
  
     [!code-csharp[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingWeatherForecast/CSharp/Window1.xaml.cs#threadingweatherupdateui)]
     [!code-vb[ThreadingWeatherForecast#ThreadingWeatherUpdateUI](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingWeatherForecast/visualbasic/window1.xaml.vb#threadingweatherupdateui)]  
  
 ときに、<xref:System.Windows.Threading.Dispatcher>で、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドに時間がある、スケジュールされた呼び出し実行`UpdateUserInterface`です。 このメソッドは、時計のアニメーションを停止し、天気を表すイメージを選択します。 イメージが表示され、「フェッチ予測」ボタンを復元します。  
  
<a name="multi_browser"></a>   
### <a name="multiple-windows-multiple-threads"></a>複数のウィンドウ、複数のスレッド  
 いくつか[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アプリケーションが複数のトップレベル ウィンドウを必要とします。 完全に 1 つのスレッドもかまわない/<xref:System.Windows.Threading.Dispatcher>複数の windows では複数のスレッドもを管理するための組み合わせが的確にしないでください。 これは、windows の 1 つで、スレッドを占有する可能性がある場合は特に当てはまります。  
  
 [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] エクスプ ローラーは、この方法で動作します。 新しい各エクスプ ローラー ウィンドウが元のプロセスに属するが、独立したスレッドの制御下で作成されます。  
  
 使用して、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] <xref:System.Windows.Controls.Frame>コントロール、ページを表示することができます。 単純なを簡単に作成できるよう[!INCLUDE[TLA2#tla_ie](../../../../includes/tla2sharptla-ie-md.md)]置換します。 重要な機能をまず: 新しいエクスプ ローラー ウィンドウを開く機能します。 ユーザーが、新しいウィンドウをクリックしたとき ボタン、別のスレッドでウィンドウのコピーを起動します。 これにより、windows のいずれかで実行時間の長いまたはブロックしている操作は、他のすべての windows をロックしません。  
  
 Web ブラウザーのモデルでは実際には、独自の複雑なスレッド モデルがあります。 ほとんどのリーダーに慣れることがあるために選択しました。  
  
 次の例では、コードを示します。  
  
 [!code-xaml[ThreadingMultipleBrowsers#ThreadingMultiBrowserXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml#threadingmultibrowserxaml)]  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsercodebehind)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserCodeBehind](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsercodebehind)]  
  
 このコードの次のスレッド セグメント、最も重要な部分では、このコンテキストのとおりです。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowsernewwindow)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserNewWindow](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowsernewwindow)]  
  
 このメソッドが呼び出されます「新しいウィンドウ」ボタンをクリックします。 新しいスレッドを作成し、それを非同期的に起動します。  
  
 [!code-csharp[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThreadingMultipleBrowsers/CSharp/Window1.xaml.cs#threadingmultibrowserthreadstart)]
 [!code-vb[ThreadingMultipleBrowsers#ThreadingMultiBrowserThreadStart](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ThreadingMultipleBrowsers/VisualBasic/Window1.xaml.vb#threadingmultibrowserthreadstart)]  
  
 このメソッドは、新しいスレッドの開始ポイントです。 このスレッドの制御下で、新しいウィンドウを作成します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 新たに自動的に作成<xref:System.Windows.Threading.Dispatcher>を新しいスレッドを管理します。 開始、ウィンドウを機能させるために必要なは、<xref:System.Windows.Threading.Dispatcher>です。  
  
<a name="stumbling_points"></a>   
## <a name="technical-details-and-stumbling-points"></a>技術的な詳細と障害点  
  
### <a name="writing-components-using-threading"></a>スレッドを使用するコンポーネントを記述  
 Microsoft .NET Framework 開発者ガイドは、コンポーネントがそのクライアントへの非同期動作を公開する方法のパターンを説明します (を参照してください[イベント ベースの非同期パターン概要](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md))。 たとえば、パッケージ化する場合、`FetchWeatherFromServer`を再利用可能なノングラフィック コンポーネントにメソッドです。 次の標準の Microsoft .NET Framework パターンには、次のようなこれはなります。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent1)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent1)]  
  
 `GetWeatherAsync` 使用など、バック グラウンド スレッドを作成する前に説明した手法のいずれかを非同期に作業を行うには、呼び出し元スレッドをブロックしていません。  
  
 このパターンの最も重要な部分の 1 つを呼び出して、 *MethodName* `Completed`メソッドを呼び出した同じスレッドで、 *MethodName* `Async`で始まるメソッド。 次を使用して[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]格納することにより、非常に簡単に<xref:System.Windows.Threading.Dispatcher.CurrentDispatcher%2A>— ノングラフィック コンポーネントでしたのみで使用されますが、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 、アプリケーションではなく[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]または[!INCLUDE[TLA#tla_aspnet](../../../../includes/tlasharptla-aspnet-md.md)]プログラムです。  
  
 <xref:System.Windows.Threading.DispatcherSynchronizationContext>クラスこのニーズに対応 — ということの簡素化されたバージョンとして<xref:System.Windows.Threading.Dispatcher>を他の動作を[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]フレームワークもします。  
  
 [!code-csharp[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CommandingOverviewSnippets/CSharp/Window1.xaml.cs#threadingarticleweathercomponent2)]
 [!code-vb[CommandingOverviewSnippets#ThreadingArticleWeatherComponent2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CommandingOverviewSnippets/visualbasic/window1.xaml.vb#threadingarticleweathercomponent2)]  
  
### <a name="nested-pumping"></a>ポンピング入れ子になった  
 ないを完全にロックして可能な場合があります、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 について考えてみます、<xref:System.Windows.MessageBox.Show%2A>のメソッド、<xref:System.Windows.MessageBox>クラスです。 <xref:System.Windows.MessageBox.Show%2A> [ok] ボタンをクリックするまでを返しません。 対話するためにメッセージ ループが必要なウィンドウは、ただし、作成します。 ユーザーが [ok] をクリックするを待つ、中に、元のアプリケーション ウィンドウはユーザー入力に応答しません。 ただし、引き続き必要が描画メッセージを処理します。 元のウィンドウには、取り除いたときにそれ自体が再描画します。  
  
 ![[OK] ボタンを含む MessageBox](../../../../docs/framework/wpf/advanced/media/threadingnestedpumping.png "ThreadingNestedPumping")  
  
 一部のスレッドは、メッセージ ボックス ウィンドウを担当する必要があります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 新しいスレッド、メッセージ ボックス ウィンドウを作成してが、このスレッドは元のウィンドウで無効になっている要素を描画することはできません (相互排他の以前のディスカッションを注意してください)。 代わりに、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]処理システム入れ子になったメッセージを使用します。 <xref:System.Windows.Threading.Dispatcher>クラスと呼ばれる特殊なメソッドが含まれています。 <xref:System.Windows.Threading.Dispatcher.PushFrame%2A>、新しいメッセージ ループを開始し、アプリケーションの現在の実行ポイントを格納します。 入れ子になったメッセージ ループが終了すると、元の後に実行が再開されます。<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>呼び出します。  
  
 ここでは、<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>への呼び出しでプログラムのコンテキストを保持<xref:System.Windows.MessageBox>.<xref:System.Windows.MessageBox.Show%2A>をバック グラウンド ウィンドウを再描画し、メッセージ ボックス ウィンドウへの入力を処理する新しいメッセージ ループを開始するとします。 ユーザーが [ok] をクリックして、ポップアップ ウィンドウをクリア、入れ子になったループの終了し、呼び出しの後にコントロールが再開されます<xref:System.Windows.MessageBox.Show%2A>です。  
  
### <a name="stale-routed-events"></a>古いイベントのルーティング  
 ルーティング イベント システム[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベントが発生したときに、ツリー全体に通知します。  
  
 [!code-xaml[InputOvw#ThreadingArticleStaticRoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InputOvw/CSharp/Page1.xaml#threadingarticlestaticroutedevent)]  
  
 楕円の上でマウスの左ボタンが押されたときに`handler2`を実行します。 後に`handler2`が終了したら、イベントに渡されます、<xref:System.Windows.Controls.Canvas>を使用してオブジェクト`handler1`それを処理します。 これは場合にのみ発生`handler2`は明示的にマーク イベント オブジェクト処理済みとして。  
  
 可能であればを`handler2`かなりのこのイベントの処理時間がかかります。 `handler2` 使用して<xref:System.Windows.Threading.Dispatcher.PushFrame%2A>を返さないため、時間を入れ子になったメッセージ ループを開始します。 場合`handler2`イベントは、このメッセージ ループするときに処理するように完了のマークは、非常に古いなっても、ツリーをイベントが渡されます。  
  
### <a name="reentrancy-and-locking"></a>再入およびロック  
 ロック メカニズム、[!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)]とまったく同じように動作しない想像のいずれかです。 期待されるスレッドのロックを要求するときに完全に操作を停止します。 実際で、スレッドは、優先度の高いメッセージ受信して処理を続行します。 これにより、デッドロックを回避し、インターフェイスの最小応答は軽度のバグの可能性が導入されています。  まれな状況が、これに関する知識は必要はありません時間の大部分 (通常、[!INCLUDE[TLA2#tla_win32](../../../../includes/tla2sharptla-win32-md.md)]ウィンドウ メッセージまたは COM STA コンポーネント) これは、知っておくと便利です。  
  
 開発者は、あると仮定して操作するため、ほとんどのインターフェイスがスレッド セーフを考慮にビルドされないを[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]複数のスレッドからはアクセスできません。 この場合は、1 つのスレッドが、予期しない時期環境の変更を行うことがあります原因でこれらが間違っている効果、<xref:System.Windows.Threading.DispatcherObject>相互排他メカニズムを解決する必要があります。 次の疑似コードについて考えてみます。  
  
 ![スレッド処理再入のダイアグラム](../../../../docs/framework/wpf/advanced/media/threadingreentrancy.png "ThreadingReentrancy")  
  
 ほとんどの時間を正しいことですが、時間[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]でこのような予期しない再入本当に問題が発生します。 特定のキー時刻に[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]呼び出し<xref:System.Windows.Threading.Dispatcher.DisableProcessing%2A>、ロックの命令を使用するには、そのスレッドの変更、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]ではなく、通常、再入のないロック[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]ロックします。  
  
 では、どうしてでした、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]チームは、この動作を選択しますか? COM STA オブジェクトと、終了処理スレッドを行うにがありました。 オブジェクトがガベージ コレクトされるときにその`Finalize`メソッドがない専用ファイナライザー スレッドで実行、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 その中に問題があります、オブジェクトの COM STA で作成された、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]でスレッドを破棄することができますのみ、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドです。 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]等しく、 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> (ここでは Win32 を使用して`SendMessage`)。 場合は、[!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]スレッドがビジー状態で、ファイナライザー スレッドが停止しているし、深刻なメモリ リークが発生、COM STA オブジェクトを破棄することはできません。 そのため、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]チーム呼び出しを行った、難しいロック動作をさせるようにします。  
  
 タスクを[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]させず、メモリ リーク、再入 everywhere をブロックしない理由は、予期しない再入を避けることができます。  
  
## <a name="see-also"></a>関連項目  
 [実行時間の長い計算のサンプルを使用して、シングル スレッド アプリケーション](http://go.microsoft.com/fwlink/?LinkID=160038)
