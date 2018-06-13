---
title: デバッグのインターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: b6297c26-7624-4431-8af4-14112d07bcd5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 991e333c53101a2be2a8a19d3960c3d0879619be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409933"
---
# <a name="debugging-interfaces"></a>デバッグのインターフェイス
ここでは、共通言語ランタイム (CLR: Common Language Runtime) で実行するプログラムのデバッグを処理するアンマネージ インターフェイスについて説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [ICLRDataEnumMemoryRegions インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)  
 呼び出し元が指定したメモリ範囲を列挙するメソッドを提供します。  
  
 [ICLRDataEnumMemoryRegionsCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)  
 メモリの指定された領域を列挙した結果の `EnumMemoryRegions` をデバッガーにレポートするコールバック メソッドを提供します。  
  
 [ICLRDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 対象の CLR プロセスと対話するためのメソッドを提供します。  
  
 [ICLRDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)  
 データ アクセス サービス層で使用して対象プロセスの仮想メモリ領域を操作する、`ICLRDataTarget` のサブクラスです。  
  
 [ICLRDataTarget3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget3-interface.md)  
 サブクラス[ICLRDataTarget2](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-interface.md)例外情報へのアクセスを提供します。  
  
 [ICLRDebugging インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-interface.md)  
 デバッグ用にモジュールの読み込みとアンロードを処理するメソッドを提供します。  
  
 [ICLRDebuggingLibraryProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-interface.md)  
 含まれています、 [ProvideLibrary メソッド](../../../../docs/framework/unmanaged-api/debugging/iclrdebugginglibraryprovider-providelibrary-method.md)メソッドで、コールバック インターフェイスの共通言語ランタイム バージョンに固有の上にロードし、要求時にデバッグ ライブラリをライブラリ プロバイダーを取得します。  
  
 [ICLRMetadataLocator インターフェイス](../../../../docs/framework/unmanaged-api/debugging/iclrmetadatalocator-interface.md)  
 データ アクセス サービス層で使用して、対象プロセス内のアセンブリのメタデータを見つけるためのインターフェイスです。  
  
 [ICorDebug インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
 開発者が CLR 環境でアプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [ICorDebugAppDomain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md)  
 アプリケーション ドメインをデバッグするためのメソッドを提供します。  
  
 [ICorDebugAppDomain2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain2-interface.md)  
 配列、ポインター、関数ポインター、および ByRef 型を使用するメソッドを提供します。 これは、`ICorDebugAppDomain` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAppDomain3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)  
 アプリケーション ドメインで [!INCLUDE[wrt](../../../../includes/wrt-md.md)] 型を操作するメソッドを提供します。 このインターフェイスは、`ICorDebugAppDomain` インターフェイスと `ICorDebugAppDomain2` インターフェイスを拡張します。  
  
 [ICorDebugAppDomain4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain4-interface.md)  
 論理的に拡張し、 [ICorDebugAppDomain](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain-interface.md) COM 呼び出し可能ラッパーからマネージ オブジェクトを取得するインターフェイスです。  
  
 [ICorDebugAppDomainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomainenum-interface.md)  
 列挙体の次の位置から、指定した数の `ICorDebugAppDomain` の値を返すメソッドを提供します。  
  
 [ICorDebugArrayValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-interface.md)  
 1 次元または多次元の配列を表す `ICorDebugHeapValue` のサブクラスです。  
  
 [ICorDebugAssembly Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)  
 アセンブリを表します。  
  
 [ICorDebugAssembly2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly2-interface.md)  
 アセンブリを表します。 これは、`ICorDebugAssembly` インターフェイスの機能を拡張するインターフェイスです。  
  
 [ICorDebugAssembly3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 論理的に拡張し、 [ICorDebugAssembly](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly-interface.md)のコンテナー アセンブリとそのコンテナー内のサポートを提供するインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugAssemblyEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugassemblyenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugAssembly` 配列を列挙します。  
  
 [ICorDebugBlockingObjectEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugblockingobjectenum-interface.md)  
 一覧については、列挙子を提供[CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md)構造体。  
  
 [ICorDebugBoxValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugboxvalue-interface.md)  
 ボックス化された値クラスのオブジェクトを表す `ICorDebugHeapValue` のサブクラス。  
  
 [ICorDebugBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-interface.md)  
 関数のブレークポイント、または値のウォッチ ポイントを表します。  
  
 [ICorDebugBreakpointEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpointenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugBreakpoint` 配列を列挙します。  
  
 [ICorDebugChain Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-interface.md)  
 物理呼び出し履歴または論理呼び出し履歴のセグメントを表します。  
  
 [ICorDebugChainEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugchainenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugChain` 配列を列挙します。  
  
 [ICorDebugClass Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass-interface.md)  
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugClass` はインスタンス化されないジェネリック型を表します。  
  
 [ICorDebugClass2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugclass2-interface.md)  
 ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。 このインターフェイスは、`ICorDebugClass` の機能を拡張します。  
  
 [ICorDebugCode Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)  
 Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。  
  
 [ICorDebugCode2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)  
 `ICorDebugCode` の機能を拡張するメソッドを提供します。  
  
 [ICorDebugCode3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 拡張メソッドを提供[ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)と[ICorDebugCode2](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-interface.md)マネージ戻り値に関する情報を提供します。  
  
 [ICorDebugCode4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)  
 ローカル変数と関数の引数を列挙するデバッガーを有効にするメソッドを提供します。  
  
 [ICorDebugCodeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcodeenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugCode` 配列を列挙します。  
  
 [ICorDebugComObjectValue のインターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugcomobjectvalue-interface.md)  
 キャッシュされたインターフェイス オブジェクトを取得するメソッドを提供します。  
  
 [ICorDebugContext Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontext-interface.md)  
 コンテキストのオブジェクトを表します。 このインターフェイスはまだ実装されていません。  
  
 [ICorDebugController Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-interface.md)  
 コードの実行コンテキストを制御できる <xref:System.Diagnostics.Process> または <xref:System.AppDomain> のスコープを表します。  
  
 [ICorDebugDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 特定のターゲット プロセスにアクセスするためのコールバック インターフェイスが用意されています。  
  
 [ICorDebugDataTarget2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)インターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugDataTarget3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget3-interface.md)  
 論理的に拡張し、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)読み込まれたモジュールに関する情報を提供するインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugDebugEvent インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)  
 すべての `ICorDebug` デバッグ イベントを派生させる基本インターフェイスを定義します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugEditAndContinueErrorInfo インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinueerrorinfo-interface.md)  
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEditAndContinueSnapshot Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeditandcontinuesnapshot-interface.md)  
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugenum-interface1.md)  
 デバッグ中の列挙子の抽象基底インターフェイスとして機能します。  
  
 [ICorDebugErrorInfoEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugerrorinfoenum-interface.md)  
 互換性のために残されています。 このインターフェイスは使用しないでください。  
  
 [ICorDebugEval Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval-interface.md)  
 デバッガーが、デバッグ中のコードのコンテキスト内でコードを実行できるメソッドを提供します。  
  
 [ICorDebugEval2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-interface.md)  
 ジェネリック型をサポートできるように `ICorDebugEval` を拡張します。  
  
 [ICorDebugExceptionDebugEvent インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)例外イベントをサポートするインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugExceptionObjectCallStackEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 例外オブジェクトに埋め込まれているコール スタックの情報の列挙子を提供します。  
  
 [ICorDebugExceptionObjectValue インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectvalue-interface.md)  
 拡張、 [ICorDebugObjectValue](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)マネージ例外オブジェクトからスタック トレース情報を提供するインターフェイスです。  
  
 [ICorDebugFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)  
 現在のスタックのフレームを表します。  
  
 [ICorDebugFrameEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugframeenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugFrame` 配列を列挙します。  
  
 [ICorDebugFunction Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md)  
 マネージ関数またはマネージ メソッドを表します。  
  
 [ICorDebugFunction2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction2-interface.md)  
 `ICorDebugFunction` を論理的に拡張して、"マイ コードのみ" ステップ実行によるデバッグをサポートします。  
  
 [ICorDebugFunction3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction3-interface.md)  
 論理的に拡張し、 [ICorDebugFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugfunction-interface1.md) ReJIT 要求からコードへのアクセスを提供するインターフェイスです。  
  
 [ICorDebugFunctionBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-interface.md)  
 関数内のブレークポイントをサポートするように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugGCReferenceEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 ガベージ コレクトされるオブジェクトの列挙子を提供します。  
  
 [ICorDebugGenericValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuggenericvalue-interface.md)  
 すべての値に適用する `ICorDebugValue` のサブクラスです。 このインターフェイスは、値に対して Get メソッドと Set メソッドを提供します。  
  
 [ICorDebugGuidToTypeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md)  
 GUID およびその対応する `ICorDebugType` オブジェクトをマップするオブジェクトの列挙子を提供します。  
  
 [ICorDebugHandleValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebughandlevalue-interface.md)  
 デバッガーが作成したガベージ コレクションのハンドルへの参照値を表す `ICorDebugReferenceValue` のサブクラスです。  
  
 [ICorDebugHeapEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)  
 マネージ ヒープのオブジェクトの列挙子を提供します。  
  
 [ICorDebugHeapSegmentEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugheapsegmentenum-interface.md)  
 マネージ ヒープのメモリ領域の列挙子を提供します。  
  
 [ICorDebugHeapValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue-interface.md)  
 CLR ガベージ コレクターによって収集されたオブジェクトを表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugHeapValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue2-interface1.md)  
 ランタイム ハンドルのサポートを提供する `ICorDebugHeapValue` の拡張機能です。  
  
 [ICorDebugHeapValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md)  
 オブジェクトのモニター ロック プロパティを公開します。  
  
 [ICorDebugILCode インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 中間言語 (IL) コードのセグメントを表します。  
  
 [ICorDebugILCode2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-interface.md)  
 論理的に拡張し、 [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)に元のメソッド IL オフセットを関数のローカル変数シグネチャに対するトークンを返すし、プロファイラーのインストルメント化された中間言語 (IL) にマップするメソッドを提供するインターフェイスオフセットします。  
  
 [ICorDebugILFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-interface.md)  
 MSIL コードのスタック フレームを表します。  
  
 [ICorDebugILFrame2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-interface.md)  
 `ICorDebugILFrame` の論理拡張機能です。  
  
 [ICorDebugILFrame3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 関数の戻り値をカプセル化するメソッドを提供します。  
  
 [ICorDebugILFrame4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe4-interface.md)  
 ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。 パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。  
  
 [ICorDebugInstanceFieldSymbol インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebuginstancefieldsymbol-interface.md)  
 インスタンス フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugInternalFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe-interface.md)  
 デバッガーのフレーム種類を識別します。  
  
 [ICorDebugInternalFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md)  
 スタックのアドレス位置に関連するなどの内部フレームに関する情報を提供[ICorDebugFrame](../../../../docs/framework/unmanaged-api/debugging/icordebugframe-interface.md)オブジェクト。  
  
 [ICorDebugLoadedModule インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugloadedmodule-interface.md)  
 読み込まれたモジュールに関する情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugManagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)  
 デバッガーのコールバックを処理するメソッドを提供します。  
  
 [ICorDebugManagedCallback2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 デバッガーの例外処理およびマネージ デバッグ アシスタント (MDA: Managed Debugging Assistants) をサポートするメソッドを提供します。 `ICorDebugManagedCallback2` は、`ICorDebugManagedCallback` の論理拡張機能です。  
  
 [ICorDebugManagedCallback3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-interface.md)  
 有効なカスタムのデバッガー通知が発生したことを示すコールバック メソッドを提供します。  
  
 [ICorDebugMDA インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)  
 マネージ デバッグ アシスタント (MDA) メッセージを表します。  
  
 [ICorDebugMemoryBuffer インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 メモリ内のバッファーを表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMergedAssemblyRecord インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmergedassemblyrecord-interface.md)  
 マージされたアセンブリに関する情報を提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugMetaDataLocator インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmetadatalocator-interface.md)  
 デバッガーにメタデータ情報を提供します。  
  
 [ICorDebugModule Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule-interface.md)  
 実行可能ファイルまたはダイナミック リンク ライブラリ (DLL: Dynamic-Link Library) のいずれかの CLR モジュールを表します。  
  
 [ICorDebugModule2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule2-interface.md)  
 `ICorDebugModule` の論理的な拡張機能として動作します。  
  
 [ICorDebugModule3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-interface.md)  
 動的モジュールのシンボル リーダーを作成します。  
  
 [ICorDebugModuleBreakpoint Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmodulebreakpoint-interface.md)  
 特定のモジュールにアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 [ICorDebugModuleDebugEvent インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
 拡張、 [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md)モジュール レベルのイベントをサポートするインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugModuleEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduleenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugModule` 配列を列挙します。  
  
 [ICorDebugMutableDataTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 拡張、 [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)変更可能なデータ ターゲットをサポートするインターフェイスです。  
  
 [ICorDebugNativeFrame Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe-interface.md)  
 ネイティブ フレームで使用される `ICorDebugFrame` の特化された実装。  
  
 [ICorDebugNativeFrame2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugnativeframe2-interface.md)  
 子と親のフレームの関係をテストするメソッドを提供します。  
  
 [ICorDebugObjectEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、オブジェクトの配列を相対仮想アドレス (RVA: Relative Virtual Address) で列挙します。  
  
 [ICorDebugObjectValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue-interface.md)  
 オブジェクトが含まれた値を表す `ICorDebugValue` のサブクラスです。  
  
 [ICorDebugObjectValue2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugobjectvalue2-interface.md)  
 継承およびオーバーライドをサポートするように `ICorDebugObjectValue` を拡張します。  
  
 [ICorDebugProcess Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)  
 マネージ コードを実行しているプロセスを表します。  
  
 [ICorDebugProcess2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess2-interface1.md)  
 `ICorDebugProcess` の論理拡張機能です。  
  
 [ICorDebugProcess3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md)  
 カスタムのデバッガー通知を制御します。  
  
 [ICorDebugProcess5 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-interface.md)  
 拡張、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)マネージ オブジェクトのガベージ コレクションに関する情報を提供して、デバッガーがアプリケーションからイメージを読み込むかどうかを決定する、マネージ ヒープへのアクセスをサポートするためにインターフェイスのローカルネイティブ イメージ キャッシュします。  
  
 [ICorDebugProcess6 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-interface.md)  
 論理的に拡張し、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)ネイティブ例外デバッグ イベントや仮想モジュール分割でエンコードされたマネージ デバッグ イベントをデコードなどの機能を有効にするインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugProcess7 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess7-interface.md)  
 ターゲット プロセスでメモリ内のメタデータ更新を処理するようにデバッガーを構成するメソッドを提供します。  
  
 [ICorDebugProcess8 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess8-interface.md)  
 論理的に拡張し、 [ICorDebugProcess](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess-interface.md)有効または無効に特定の種類のインターフェイス[ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)例外コールバック。  
  
 [ICorDebugProcessEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugprocessenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugProcess` 配列を列挙します。  
  
 [ICorDebugReferenceValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugreferencevalue-interface.md)  
 参照型をサポートする `ICorDebugValue` のサブクラス。  
  
 [ICorDebugRegisterSet インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md)  
 現在コードを実行しているマシン上で使用できるレジスタ セットを表します。  
  
 [ICorDebugRegisterSet2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset2-interface.md)  
 64 を超えるレジスタを持つハードウェア プラットフォーム用に `ICorDebugRegisterSet` の機能を拡張します。  
  
 [ICorDebugRemote インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremote-interface.md)  
 リモート ターゲット プロセスに対してマネージ デバッガーを起動または接続する機能を提供します。  
  
 [ICorDebugRemoteTarget インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 開発者が CLR 環境で Silverlight ベース アプリケーションをデバッグできるようにするメソッドを提供します。  
  
 [ICorDebugRuntimeUnwindableFrame インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugruntimeunwindableframe-interface.md)  
 共通言語ランタイム (CLR: Common Language Runtime) でフレームをアンワインドする必要のあるアンマネージ メソッドに対してサポートを提供します。  
  
 [ICorDebugStackWalk インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)  
 スレッドのスタック上のマネージ メソッド (フレーム) を取得するメソッドを提供します。  
  
 [ICorDebugStaticFieldSymbol インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 静的フィールドのデバッグ シンボル情報を表します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugStepper Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-interface.md)  
 デバッガーが実行するコード実行内のステップを表します。コマンドの発行から完了までの間は識別子として機能します。これを使用するとステップをキャンセルできます。  
  
 [ICorDebugStepper2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper2-interface1.md)  
 マイ コードのみ (JMC: Just My Code) デバッグのサポートを提供します。  
  
 [ICorDebugStepperEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstepperenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugStepper` 配列を列挙します。  
  
 [ICorDebugStringValue Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-interface.md)  
 文字列値に適用する `ICorDebugHeapValue` のサブクラスです。  
  
 [ICorDebugSymbolProvider インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 デバッグ シンボル情報を取得するために使用できるメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugSymbolProvider2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider2-interface.md)  
 論理的に拡張し、 [ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)追加のデバッグ シンボル情報を取得するインターフェイスです。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugThread Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-interface.md)  
 プロセス内のスレッドを表します。 `ICorDebugThread` インスタンスの有効期間は、それが表しているスレッドの有効期間と同じです。  
  
 [ICorDebugThread2 Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interface.md)  
 `ICorDebugThread` の論理的な拡張機能として動作します。  
  
 [ICorDebugThread3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-interface.md)  
 エントリ ポイントを提供、 [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md)と対応するインターフェイスです。  
  
 [ICorDebugThread4 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugthread4-interface.md)  
 スレッドのブロック情報を提供します。  
  
 [ICorDebugThreadEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugthreadenum-interface1.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugThread` 配列を列挙します。  
  
 [ICorDebugType Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)  
 基本型または複合型 (つまり、ユーザー定義) のいずれかの型を表します。 型がジェネリックの場合、`ICorDebugType` はインスタンス化されたジェネリック型を表します。  
  
 [ICorDebugType2 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)  
 拡張、 [ICorDebugType](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-interface.md)基本データ型または複合 (ユーザー定義) の型の型の識別子を取得するインターフェイスです。  
  
 [ICorDebugTypeEnum Interface1](../../../../docs/framework/unmanaged-api/debugging/icordebugtypeenum-interface.md)  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugType` 配列を列挙します。  
  
 [ICorDebugUnmanagedCallback インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-interface.md)  
 CLR に直接関連していないネイティブ イベントについて通知します。  
  
 "ICorDebugValue"  
 デバッグ中のプロセス内の読み取り値または書き込み値を表します。  
  
 "ICorDebugValue2"  
 `ICorDebugValue` をサポートできるように `ICorDebugType` を拡張します。  
  
 [ICorDebugValue3 インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue3-interface.md)  
 2 GB よりも大きな配列をサポートする"ICorDebugValue"および"ICorDebugValue2"インターフェイスを拡張します。  
  
 "ICorDebugValueBreakpoint"  
 特定の値にアクセスできるように `ICorDebugBreakpoint` を拡張します。  
  
 "ICorDebugValueEnum"  
 `ICorDebugEnum` メソッドを実装し、`ICorDebugValue` 配列を列挙します。  
  
 [ICorDebugVariableHome インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 ローカル変数または関数の引数を表します。  
  
 [ICorDebugVariableHomeEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 ローカル変数と関数の引数、列挙子を提供します。  
  
 [ICorDebugVariableSymbol インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 変数のデバッグ シンボル情報を取得します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorDebugVirtualUnwinder インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icordebugvirtualunwinder-interface.md)  
 スタック アンワインドを支援するメソッドを提供します。 **.NET ネイティブのみで使用できます。**  
  
 [ICorPublish インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)  
 発行プロセスの汎用インターフェイスとして機能します。  
  
 [ICorPublishAppDomain インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomain-interface.md)  
 アプリケーション ドメインの情報を表し、提供します。  
  
 [ICorPublishAppDomainEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishappdomainenum-interface.md)  
 現在プロセス内に存在する `ICorPublishAppDomain` オブジェクトのコレクションを走査するメソッドを提供します。  
  
 [ICorPublishEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishenum-interface.md)  
 発行する列挙子の抽象ベースとして機能します。  
  
 [ICorPublishProcess インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md)  
 プロセスの情報にアクセスするメソッドを適用します。  
  
 [ICorPublishProcessEnum インターフェイス](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocessenum-interface.md)  
 `ICorPublishProcess` オブジェクトのコレクションを走査するメソッドを提供します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [列挙型のデバッグ](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
