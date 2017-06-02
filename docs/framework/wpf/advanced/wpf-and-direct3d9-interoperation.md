---
title: "WPF と Direct3D9 の相互運用性 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Direct3D9 [WPF 相互運用性], 作成 (Direct3D9 コンテンツを)"
  - "WPF, 作成 (Direct3D9 コンテンツを)"
ms.assetid: 1b14b823-69c4-4e8d-99e4-f6dade58f89a
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 25
---
# WPF と Direct3D9 の相互運用性
Windows Presentation Foundation \(WPF\) アプリケーションの中に Direct3D9 コンテンツを含めることができます。  このトピックでは、WPF と効率よく相互運用するための Direct3D9 コンテンツを作成する方法について説明します。  
  
> [!NOTE]
>  Direct3D9 コンテンツを WPF で使用するときは、パフォーマンスについても考慮する必要があります。  パフォーマンスを最適化する方法の詳細については、「[Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)」を参照してください。  
  
## 表示バッファー  
 <xref:System.Windows.Interop.D3DImage> クラスは、*バック バッファー*および*フロント バッファー*と呼ばれる 2 種類の表示バッファーを管理します。  バック バッファーはユーザーの Direct3D9 サーフェイスです。  バック バッファーへの変更点は、<xref:System.Windows.Interop.D3DImage.Unlock%2A> メソッドを呼び出すときに、フロント バッファーにコピーされます。  
  
 次の図は、バック バッファーとフロント バッファーの関係を示しています。  
  
 ![D3DImage 表示バッファー](../../../../docs/framework/wpf/advanced/media/d3dimage-buffers.png "D3DImage\_buffers")  
  
## Direct3D9 デバイスの作成  
 Direct3D9 コンテンツを表示するには、Direct3D9 デバイスを作成する必要があります。  デバイスを作成するために使用できる Direct3D9 オブジェクトには、`IDirect3D9` と `IDirect3D9Ex` の 2 種類があります。  これらのオブジェクトを使用して、`IDirect3DDevice9` デバイスと `IDirect3DDevice9Ex` デバイスを作成します。  
  
 次のいずれかのメソッドを呼び出すことで、デバイスを作成します。  
  
-   `IDirect3D9 * Direct3DCreate9(UINT SDKVersion);`  
  
-   `HRESULT Direct3DCreate9Ex(UINT SDKVersion, IDirect3D9Ex **ppD3D);`  
  
 Windows Vista または後で、Windows オペレーティング システム Driver Display Model \(WDDM\) を使用するようにコンフィギュレーションされていると `Direct3DCreate9Ex` の表示方法を使用します。  それ以外のすべてのプラットフォームでは、`Direct3DCreate9` メソッドを使用します。  
  
### Direct3DCreate9Ex メソッドの可用性  
 d3d9.dll に Windows Vista またはそれ以降のオペレーティング システムでのみ `Direct3DCreate9Ex` の方法があります。  この関数を Windows XP で直接リンクすると、アプリケーションの読み込みが失敗します。  `Direct3DCreate9Ex` メソッドがサポートされているかどうかを確認するには、この DLL を読み込み、プロシージャ アドレスを探します。  次のコードは、`Direct3DCreate9Ex` メソッドをテストする方法を示しています。  完全なコード例については、「[チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)」を参照してください。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureD3DObjects](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensured3dobjects)]  
  
### HWND の作成  
 デバイスを作成するには、HWND が必要です。  通常は、使用する Direct3D9 用のダミー HWND を作成します。  次のコード例は、ダミー HWND を作成する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_EnsureHWND](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_ensurehwnd)]  
  
### 表示パラメーター  
 デバイスを作成するには `D3DPRESENT_PARAMETERS` 構造体も必要ですが、重要なのは一部のパラメーターだけです。  これらのパラメーターは、メモリの使用量を最小限に抑えるために選択されています。  
  
 `BackBufferHeight` フィールドおよび `BackBufferWidth` フィールドを 1 に設定します。  これらを 0 に設定すると、HWND のサイズが設定されます。  
  
 Direct3D9 によって使用されるメモリの破棄と Direct3D9 による FPU 設定の変更を回避するために、`D3DCREATE_MULTITHREADED` フラグと `D3DCREATE_FPU_PRESERVE` フラグを常に設定します。  
  
 次のコードは、`D3DPRESENT_PARAMETERS` 構造体を初期化する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_Init](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_init)]  
  
## バック バッファーのレンダリング先の作成  
 <xref:System.Windows.Interop.D3DImage> 内の Direct3D9 コンテンツを表示するには、Direct3D9 サーフェイスを作成し、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> メソッドを呼び出してそれを割り当てます。  
  
### アダプターによるサポートの確認  
 サーフェイスを作成する前に、必要なサーフェイス プロパティがすべてのアダプターでサポートされていることを確認します。  レンダリング先として 1 つのアダプターだけを指定した場合でも、WPF ウィンドウはシステム内のどのアダプターでも表示できます。  WPF では使用可能なアダプター間でサーフェイスを移動することがあるので、マルチアダプター構成を処理する Direct3D9 コードを常に記述し、すべてのアダプターのサポート状況を確認してください。  
  
 次のコード例は、システムのすべてのアダプターで Direct3D9 がサポートされているかどうかを調べる方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_TestSurfaceSettings](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_testsurfacesettings)]  
  
### サーフェイスの作成  
 サーフェイスを作成する前に、デバイスが対象のオペレーティング システム上で適切なパフォーマンスで動作できることを確認します。  詳細については、「[Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)」を参照してください。  
  
 デバイスの能力を確認した後、サーフェイスを作成できます。  次のコード例は、レンダリング先を作成する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#Renderer_CreateSurface](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderer.cpp#renderer_createsurface)]  
  
### WDDM  
 WDDM を使用するようにコンフィギュレーションされた後のオペレーティング システムと Windows Vista でレンダー ターゲットのテクスチャを作成し、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法にレベルを 0 の標的を渡すことができます。  Windows XP では、ロック可能なレンダリング先のテクスチャを作成できず、パフォーマンスが低下するので、この方法はお勧めしません。  
  
## デバイス状態の処理  
 <xref:System.Windows.Interop.D3DImage> クラスは、*バック バッファー*および*フロント バッファー*と呼ばれる 2 種類の表示バッファーを管理します。  バック バッファーは、ユーザーの Direct3D サーフェイスです。   は、バッファの変更がフロント バッファへのハードウェアに表示される <xref:System.Windows.Interop.D3DImage.Unlock%2A> 方法を追加すると、コピーようになります。  場合によっては、バッファ フロントは使用できなくなります。  デバイスが使用できなくなる原因としては、画面のロック、全画面表示の専用 Direct3D アプリケーション、ユーザーの切り替え、その他のシステムの動作が考えられます。  このような場合は、の WPF のアプリケーションは <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> イベントの処理によって通知されます。  自分のアプリケーションで使用できなくなるフロント バッファに対応する方法を WPF がソフトウェアの表示にはあることを可能にするかによって異なります。  <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> 方法に WPF は、ソフトウェアの表示にはあるかどうかを指定するパラメータを受け取る過負荷があります。  
  
 <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%29> の過負荷に電話または `false`に設定 `enableSoftwareFallback` パラメータの <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 過負荷の名前を表示するとシステムはフロント バッファが使用できないになり、何も表示されない場合は、バッファへの参照をリリースします。  フロント バッファが再び使用可能な場合、表示のシステムは、WPF のアプリケーションを通知するために <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> のイベントを上げます。  有効な Direct3D が直面すると、再び表示を再開するに <xref:System.Windows.Interop.D3DImage.IsFrontBufferAvailableChanged> のイベントのイベント ハンドラーを作成できます。  表示を再開するには、<xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A>を追加する必要があります。  
  
 `true`に設定 `enableSoftwareFallback` パラメータの <xref:System.Windows.Interop.D3DImage.SetBackBuffer%28System.Windows.Interop.D3DResourceType%2CSystem.IntPtr%2CSystem.Boolean%29> 過負荷の名前を表示するとシステムはフロント バッファが再び使用可能な場合フロント バッファが使用できなくなっている場合は、バッファへの参照は存在するが <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> を追加する必要残しません。  
  
 ソフトウェアの表示が有効の場合、ユーザーのデバイスが使用できなくなる、システムが表示 Direct3D が直面への参照を終了ステータスがあります。  Direct3D9 デバイスが利用不可かどうかを確認するには、`TestCooperativeLevel` 方法を追加します。  `TestCooperativeLevel` 方法が常に非難され、成功を返すこと、Direct3D9Ex デバイスを確認するには `CheckDeviceState` 方法を追加します。  ユーザーのデバイスが使用できなくなっている場合は、バッファに WPF の参照をリリースするに <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> を追加します。  自分のデバイスをリセットする必要がある場合は `null`に設定 `backBuffer` パラメータの <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> と呼ばれる次に `backBuffer` の <xref:System.Windows.Interop.D3DImage.SetBackBuffer%2A> を設定します Direct3D に再度有効な標的を追加します。  
  
 無効なデバイスから回復するための `Reset` メソッドの呼び出しは、マルチアダプターのサポートを実装する場合のみ実行します。  それ以外の場合は、すべての Direct3D9 インターフェイスを解放し、全体を再作成します。  アダプターのレイアウトが変更されている場合、変更前に作成された Direct3D9 オブジェクトは更新されません。  
  
## サイズ変更の処理  
 <xref:System.Windows.Interop.D3DImage> が、のサイズ以外の決済に表示されている場合、期限内に <xref:System.Windows.Media.RenderOptions.BitmapScalingMode%2A>に従って縮小増幅されますが、例外と、<xref:System.Windows.Media.Effects.SamplingMode> は <xref:System.Windows.Media.BitmapScalingMode>の代わりになります。  
  
 高い忠実性が必要な場合は、<xref:System.Windows.Interop.D3DImage> のコンテナーのサイズが変更されたときに新しいサーフェイスを作成する必要があります。  
  
 サイズ変更を処理する方法には、以下の 3 つがあります。  
  
-   レイアウト システムを処理し、サイズが変更されたときに新しいサーフェイスを作成します。  ビデオ メモリの不足や断片化が発生する可能性があるので、作成するサーフェイスが多くなりすぎないようにしてください。  
  
-   一定期間待機してサイズ変更イベントが発生しないことを確認した後、新しいサーフェイスを作成します。  
  
-   コンテナーのサイズを 1 秒間に数回チェックする <xref:System.Windows.Threading.DispatcherTimer> を作成します。  
  
## マルチモニターの最適化  
 レンダリング システムが <xref:System.Windows.Interop.D3DImage> を別のモニターに移動したときに、パフォーマンスが大幅に低下する場合があります。  
  
 WDDM の場合、移動前後のモニターが同じビデオ カード上にあり、`Direct3DCreate9Ex` を使用している限り、パフォーマンスが低下することはありません。  モニターが別々のビデオ カードを使用している場合は、パフォーマンスが低下します。  Windows XP の場合、パフォーマンスは常に低下します。  
  
 <xref:System.Windows.Interop.D3DImage> が別のモニターに移動するときは、対応するアダプター上に新しいサーフェイスを作成することで、パフォーマンスを維持できます。  
  
 パフォーマンスの低下を回避するには、マルチモニター用に特別なコードを記述します。  次のリストは、マルチモニター コードを記述するための 1 つの方法を示しています。  
  
1.  <xref:System.Windows.Interop.D3DImage> の画面空間でのポイントを、`Visual.ProjectToScreen` メソッドを使用して検出します。  
  
2.  `MonitorFromPoint` GDI メソッドを使用して、そのポイントを表示しているモニターを検出します。  
  
3.  `IDirect3D9::GetAdapterMonitor` メソッドを使用して、モニターがオンになっている Direct3D9 アダプターを検出します。  
  
4.  検出されたアダプターがバック バッファーを持つアダプターと一致しない場合は、新しいモニターに新しいバック バッファーを作成し、それを <xref:System.Windows.Interop.D3DImage> バック バッファーに割り当てます。  
  
> [!NOTE]
>  <xref:System.Windows.Interop.D3DImage> がモニター間にまたがる場合、WDDM と `IDirect3D9Ex` が同一のアダプター上にあるときを除いてパフォーマンスは低下します。  このような状況では、パフォーマンスを向上させる方法はありません。  
  
 次のコード例は、現在のモニターを検出する方法を示しています。  
  
 [!code-cpp[System.Windows.Interop.D3DImage#RendererManager_SetAdapter](../../../../samples/snippets/cpp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/cpp/renderermanager.cpp#renderermanager_setadapter)]  
  
 <xref:System.Windows.Interop.D3DImage> コンテナーのサイズまたは位置が変更されたとき、モニターを更新します。または、1 秒間に数回更新を行う `DispatcherTimer` を使用してモニターを更新します。  
  
## WPF ソフトウェアのレンダリング  
 WPF は、次のような場合、ソフトウェアの UI スレッドで同期的にレンダリングします。  
  
-   印刷  
  
-   <xref:System.Windows.Media.Effects.BitmapEffect>  
  
-   <xref:System.Windows.Media.Imaging.RenderTargetBitmap>  
  
 これらの状況のいずれかが発生すると、レンダリング システムは <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> メソッドを呼び出して、ハードウェア バッファーをソフトウェアにコピーします。  既定の実装では、`GetRenderTargetData` メソッドをサーフェイスを使用して呼び出します。  この呼び出しはロック\/ロック解除パターンの外部で発生するので、失敗する場合があります。  この場合、`CopyBackBuffer` メソッドは `null` を返し、イメージは表示されません。  
  
 <xref:System.Windows.Interop.D3DImage.CopyBackBuffer%2A> メソッドをオーバーライドして基本実装を呼び出すことができ、`null` が返された場合はプレースホルダー <xref:System.Windows.Media.Imaging.BitmapSource> を返すことができます。  
  
 基本実装を呼び出す代わりに、独自のソフトウェア レンダリングを実装することもできます。  
  
> [!NOTE]
>  WPF がソフトウェア内で完全にレンダリングを実行する場合、WPF にフロント バッファーがないために <xref:System.Windows.Interop.D3DImage> は表示されません。  
  
## 参照  
 <xref:System.Windows.Interop.D3DImage>   
 [Direct3D9 および WPF の相互運用性のパフォーマンスに関する考慮事項](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)   
 [チュートリアル : WPF でホストするための Direct3D9 コンテンツの作成](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md)   
 [チュートリアル : WPF での Direct3D9 コンテンツのホスト](../../../../docs/framework/wpf/advanced/walkthrough-hosting-direct3d9-content-in-wpf.md)