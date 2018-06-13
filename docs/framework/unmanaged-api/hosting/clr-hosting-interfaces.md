---
title: CLR ホスト インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework hosting], version 2.0
- hosting interfaces [.NET Framework], version 2.0
- .NET Framework 2.0, hosting interfaces
ms.assetid: 703b8381-43db-4a4d-9faa-cca39302d922
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03839a2c6e52f9d2dcdd2e0941ff4fdbeb8a3a17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435642"
---
# <a name="clr-hosting-interfaces"></a>CLR ホスト インターフェイス
このセクションの内容がアンマネージ インターフェイスについて説明しますホストを使用して、共通言語ランタイム (CLR) をアプリケーションに統合します。 情報は、.NET Framework バージョン 2.0 およびそれ以降のバージョンに関連します。 これらのインターフェイスは、ランタイムは、バージョン 1.0 および 1.1 よりも多くの面を制御するホストを有効にし、CLR とホストの実行モデルの間でより緊密に統合を提供します。  
  
 .NET framework version 1.0 および 1.1 では、ホスティング モデルには、プロセス、イベント通知を受信して、特定の設定を構成するに CLR を読み込むアンマネージ ホストが有効になります。 ただし、一般に、ホストと CLR 個別に実行されてそのプロセスにします。 .NET Framework バージョン 2.0 以降のバージョンでは、新しい抽象化レイヤーは、多くの Win32 アセンブリ内の型によって現在提供されているリソースを提供し、ホストが構成可能な機能のセットを拡張、ホストを使用できます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [IActionOnCLREvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-interface.md)  
 登録されたイベントのコールバックを実行するメソッドを提供します。  
  
 [IApartmentCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iapartmentcallback-interface.md)  
 アパートメント内でコールバックを行うためのメソッドを提供します。  
  
 [IAppDomainBinding インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iappdomainbinding-interface.md)  
 実行時構成の設定方法を提供します。  
  
 [ICatalogServices インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icatalogservices-interface.md)  
 サービス カタログを作成する方法を提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ICLRAssemblyIdentityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md)  
 ホストと、CLR アセンブリの間の通信をサポートするメソッドを提供します。  
  
 [ICLRAssemblyReferenceList インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyreferencelist-interface.md)  
 ホストではなく、CLR によって読み込まれるアセンブリの一覧を管理します。  
  
 [ICLRControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 ホストに、アクセスを CLR のさまざまな側面を構成するためのメソッドを提供します。  
  
 [ICLRDebugManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrdebugmanager-interface.md)  
 識別子と表示名に一連のタスクを関連付けるホストを有効にするメソッドを提供します。  
  
 [ICLRErrorReportingManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrerrorreportingmanager-interface.md)  
 ホストがエラー報告用のカスタム ヒープ ダンプを設定できるようにするメソッドを提供します。  
  
 [ICLRGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md)  
 ホストが、CLR のガベージ コレクション システムとやり取りできるようにするメソッドを提供します。  
  
 [ICLRHostBindingPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md)  
 ホストを評価し、アセンブリのポリシー情報の変更を伝達するためのメソッドを提供します。  
  
 [ICLRHostProtectionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrhostprotectionmanager-interface.md)  
 特定のマネージ クラス、メソッド、プロパティ、およびフィールド部分的に信頼されたコードでの実行をブロックするホストを有効にします。  
  
 [ICLRIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-interface.md)  
 ホストが、指定された I/O 要求の状態の CLR に通知を有効にするコールバック メソッドを実装します。  
  
 [ICLRMemoryNotificationCallback インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-interface.md)  
 ホストが、Win32 のような方法を使用してメモリ不足の状態を報告できるように`CreateMemoryResourceNotification`関数。  
  
 [ICLROnEventManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclroneventmanager-interface.md)  
 ホストが登録および CLR イベントのコールバックを登録解除できるようにするメソッドを提供します。  
  
 [ICLRPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrpolicymanager-interface.md)  
 ホスト ポリシーのエラーやタイムアウトが発生した場合に実行されるアクションを指定できるようにするメソッドを提供します。  
  
 [ICLRProbingAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrprobingassemblyenum-interface.md)  
 ホストを作成またはその id を認識することがなく、clr の内部にあるアセンブリの id 情報を使用して、アセンブリの検索 id を取得できるようにするメソッドを提供します。  
  
 [ICLRReferenceAssemblyEnum インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrreferenceassemblyenum-interface.md)  
 ホスト ファイルを作成またはその id を認識することがなく、clr の内部にあるアセンブリの id データを使用して、ストリームで参照されるアセンブリのセットを操作できるようにするメソッドを提供します。  
  
 [ICLRRuntimeHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)  
 同様の機能を提供[ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)、ホスト コントロールのインターフェイスを設定する追加のメソッドを使用します。  
  
 [ICLRSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)  
 ホストとの同期の実装でデッドロックを検出するために要求されたタスクに関する情報を取得するためのメソッドを提供します。  
  
 [ICLRTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md)  
 ホストまたは関連付けられているタスクは、CLR に通知を提供する、CLR の要求を行うことができるようにするメソッドを提供します。  
  
 [ICLRTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrtaskmanager-interface.md)  
 ホストが CLR に新しいタスクを作成し、現在実行中のタスクを取得し、地理的な言語とタスクのカルチャ設定を明示的に要求できるようにするメソッドを提供します。  
  
 [ICLRValidator インターフェイス](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)  
 ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。  
  
 [ICorConfiguration インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)  
 CLR を構成するためのメソッドを提供します。  
  
 [ICorThreadpool インターフェイス](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)  
 スレッド プールにアクセスするためのメソッドを提供します。  
  
 [IDebuggerInfo インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerinfo-interface.md)  
 デバッグ サービスの状態に関する情報を取得するためのメソッドを提供します。  
  
 [IDebuggerThreadControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/idebuggerthreadcontrol-interface.md)  
 デバッグ サービスによるスレッドのブロックおよびブロックについて、ホストを通知するメソッドを提供します。  
  
 [IGCHost インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost-interface.md)  
 ガベージ コレクション システムに関する情報を取得して、ガベージ コレクションの一部の側面を制御するためのメソッドを提供します。  
  
 [IGCHost2 インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchost2-interface.md)  
 提供、 [SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md)メソッドにより、ガベージ コレクション セグメントのサイズと、ガベージ コレクション システムのジェネレーション 0 の最大サイズに設定する値を超えるホストを`DWORD`です。  
  
 [IGCHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md)  
 仮想メモリの制限を変更するホストに要求、ガベージ コレクターをできるようにするメソッドを提供します。  
  
 [IGCThreadControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md)  
 それ以外の場合のみがブロックされるガベージ コレクションのスレッドのスケジューリングに参加するためのメソッドを提供します。  
  
 [IHostAssemblyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblymanager-interface.md)  
 ホストが CLR またはホストに読み込む必要のあるアセンブリのセットを指定できるようにするメソッドを提供します。  
  
 [IHostAssemblyStore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostassemblystore-interface.md)  
 アセンブリと CLR とは無関係にモジュールの読み込みをホストできるようにするメソッドを提供します。  
  
 [IHostAutoEvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-interface.md)  
 ホストによって実装される自動リセット イベントの表現を提供します。  
  
 [IHostControl インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcontrol-interface.md)  
 アセンブリの読み込みを設定して、ホストがサポートするホスト インターフェイスを決定するためのメソッドを提供します。  
  
 [IHostCrst インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostcrst-interface.md)  
 スレッド処理の重要なセクションのホストの表現として機能します。  
  
 [IHostGCManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostgcmanager-interface.md)  
 ガベージ コレクションのメカニズムが CLR によって実装内のイベントのホストに通知するメソッドを提供します。  
  
 [IHostIoCompletionManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 I/O 完了ポートがホストによって提供されると対話する CLR を有効にするメソッドを提供します。  
  
 [IHostMalloc インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmalloc-interface.md)  
 CLR ホストを通じてヒープから詳細な割り当てを要求するためのメソッドを提供します。  
  
 [IHostManualEvent インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)  
 手動リセット イベントの形式のホストの実装を提供します。  
  
 [IHostMemoryManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 CLR を通じて、標準の Win32 仮想メモリ関数を使用する代わりに、ホストの仮想メモリ要求を行うためのメソッドを提供します。  
  
 [IHostPolicyManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostpolicymanager-interface.md)  
 ホストの場合、CLR を実行する操作の中止、タイムアウト、またはエラーを通知するメソッドを提供します。  
  
 [IHostSecurityContext インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 ホストによって実装されているセキュリティ コンテキスト情報を維持するために CLR を有効にします。  
  
 [IHostSecurityManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)  
 アクセスを有効にして、現在実行中のスレッドのセキュリティ コンテキストを制御するメソッドを提供します。  
  
 [IHostSemaphore インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsemaphore-interface.md)  
 ホストによって実装されるセマフォの表現を提供します。  
  
 [IHostSyncManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)  
 CLR、Win32 の同期の関数を使用する代わりに、ホストを呼び出すことによって同期プリミティブを作成するためのメソッドを提供します。  
  
 [IHostTask インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md)  
 タスクを管理するホストと通信するために CLR を有効にするメソッドを提供します。  
  
 [IHostTaskManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihosttaskmanager-interface.md)  
 標準のオペレーティング システムのスレッドやファイバーの関数を使用する代わりに、ホストを通じてタスクを使用する CLR を有効にするメソッドを提供します。  
  
 [IHostThreadPoolManager インターフェイス](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 CLR スレッド プールを構成して、スレッド プールに作業項目をキューに登録する方法を提供します。  
  
 [IManagedObject インターフェイス](../../../../docs/framework/unmanaged-api/hosting/imanagedobject-interface.md)  
 マネージ オブジェクトを制御するためのメソッドを提供します。  
  
 "IObjectHandle"  
 メソッドをラップ解除の値渡しでマーシャ リング オブジェクトの間接参照を提供します。  
  
 [ITypeName インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypename-interface.md)  
 型名の情報を取得するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ITypeNameBuilder インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypenamebuilder-interface.md)  
 型名を構築するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 [ITypeNameFactory インターフェイス](../../../../docs/framework/unmanaged-api/hosting/itypenamefactory-interface.md)  
 型名を分解するためのメソッドを提供します。 (このインターフェイスは、.NET Framework インフラストラクチャをサポートしているし、コードから直接使用するものではありません)。  
  
 "IValidator"  
 ポータブル実行可能 (PE) イメージを検証し、検証エラーを報告のメソッドを提供します。  
  
## <a name="related-sections"></a>関連項目  
 
  [非推奨の CLR のホスト インターフェイスおよびコクラス](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-interfaces-and-coclasses.md)  
 .NET Framework version 1.0 および 1.1 で提供されるホスト インターフェイスを説明するトピックが含まれています。  
  
 [.NET Framework 4 および 4.5 で追加された CLR ホスト インターフェイス](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 提供されるホスト インターフェイスを説明するトピックが含まれています、[!INCLUDE[net_v40_short](../../../../includes/net-v40-short-md.md)]です。
