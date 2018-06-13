---
title: 列挙体のデバッグ
ms.date: 03/30/2017
helpviewer_keywords:
- debugging enumerations [.NET Framework]
- unmanaged enumerations [.NET Framework], debugging
- enumerations [.NET Framework debugging]
ms.assetid: 3af9f584-f1b4-4154-aeaa-8fce7c9f8b50
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b81e7c2ffabdee78af34d00c48fb29c7525dea08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33410469"
---
# <a name="debugging-enumerations"></a>列挙体のデバッグ
このセクションでは、デバッグ API が使用するアンマネージ列挙体について説明します。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [CLR_DEBUGGING_PROCESS_FLAGS 列挙型](../../../../docs/framework/unmanaged-api/debugging/clr-debugging-process-flags-enumeration.md)  
 によって使用されている値を提供、 [iclrdebugging::openvirtualprocess](../../../../docs/framework/unmanaged-api/debugging/iclrdebugging-openvirtualprocess-method.md)メソッドです。  
  
 [CLRDataEnumMemoryFlags 列挙型](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md)  
 メモリ領域への呼び出しを示す、 [iclrdataenummemoryregions::enummemoryregions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md)メソッドに含める必要があります。  
  
 [COR_PUB_ENUMPROCESS 列挙型](../../../../docs/framework/unmanaged-api/debugging/cor-pub-enumprocess-enumeration.md)  
 列挙するプロセスの型を識別します。  
  
 [CorDebugBlockingReason 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingreason-enumeration.md)  
 指定されたオブジェクト上でスレッドがブロックされる理由を指定します。  
  
 CorDebugChainReason  
 呼び出しチェーンが開始する理由を示します。  
  
 [CorDebugCodeInvokeKind 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokekind-enumeration.md)  
 エクスポートされた関数がマネージ コードを呼び出す方法を示します。  
  
 [CorDebugCodeInvokePurpose 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugcodeinvokepurpose-enumeration.md)  
 エクスポートされた関数がマネージ コードを呼び出す理由を示します。  
  
 CorDebugCreateProcessFlags  
 呼び出しで使用できる追加のデバッグ オプションを提供、 [icordebug::createprocess](../../../../docs/framework/unmanaged-api/debugging/icordebug-createprocess-method.md)メソッドです。  
  
 [CorDebugDebugEventKind 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md)  
 情報がデコードされるによってイベントの種類を示す、 [DecodeEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-decodeevent-method.md)メソッドです。  
  
 [CorDebugDecodeEventFlagsWindows 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugdecodeeventflagswindows-enumeration.md)  
 Windows プラットフォームのデバッグ イベントに関する追加情報を提供します。  
  
 CorDebugExceptionCallbackType  
 指定されたコールバックの型を示す、 [icordebugmanagedcallback 2::exception](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-exception-method.md)イベント。  
  
 [CorDebugExceptionFlags 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionflags-enumeration.md)  
 例外に関する追加情報を提供します。  
  
 CorDebugExceptionUnwindCallbackType  
 アンワインド フェーズ中にコールバックによって通知されるイベントを示します。  
  
 [CorDebugGCType 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebuggctype-enumeration.md)  
 ガベージ コレクターがワークステーションまたはサーバーのどちらで実行されているかを示します。  
  
 [CorDebugGenerationTypes 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebuggenerationtypes-enumeration.md)  
 マネージ ヒープ上のメモリ領域の生成を指定します。  
  
 CorDebugHandleType  
 ハンドル型を示します。  
  
 [CorDebugIlToNativeMappingTypes 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md)  
 ネイティブ命令の特定の範囲が特別なコード領域に対応するかどうかを示します。  
  
 CorDebugIntercept  
 ステップ インできるコードの型を示します。  
  
 [CorDebugInterfaceVersion 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebuginterfaceversion-enumeration.md)  
 .NET Framework のバージョン、またはインターフェイスが導入された .NET Framework のバージョンのいずれかを指定します。  
  
 CorDebugInternalFrameType  
 スタック フレームの型を示します。  
  
 [CorDebugJITCompilerFlags 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)  
 マネージ Just-In-Time (JIT) コンパイラの動作に影響を与える値が含まれます。  
  
 [CorDebugJITCompilerFlagsDeprecated 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflagsdeprecated-enumeration.md)  
 互換性のために残されています。 使用して、`CORDEBUG_JIT_DEFAULT`のメンバー、 [CorDebugJITCompilerFlags](../../../../docs/framework/unmanaged-api/debugging/cordebugjitcompilerflags-enumeration.md)列挙代わりにします。  
  
 CorDebugMappingResult  
 命令ポインター (IP) の値が得られた方法の詳細を提供します。  
  
 [CorDebugMDAFlags 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugmdaflags-enumeration.md)  
 マネージ デバッグ アシスタント (MDA) が生成されるスレッドのステータスを指定します。  
  
 [CorDebugNGenPolicy 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugngenpolicy-enumeration.md)  
 デバッガーがネイティブ イメージ キャッシュからネイティブ (NGen) イメージを読み込むかどうかを指定する値を提供します。  
  
 [CorDebugPlatform 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugplatform-enumeration.md)  
 使用されるターゲット プラットフォームの値を提供、 [icordebugdatatarget::getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md)メソッドです。  
  
 [CorDebugRecordFormat 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
 ネイティブ例外デバッグ イベントに関する情報を格納するバイト配列内のデータの形式を示します。  
  
 CorDebugRegister  
 指定されたプロセッサ アーキテクチャに関連付けられたレジスタを指定します。  
  
 [CorDebugSetContextFlag 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugsetcontextflag-enumeration.md)  
 スタック上のアクティブ (またはリーフ) フレーム上からのコンテキストなのか、別のフレームからのアンワインドにより計算されたコンテキストなのかを示します。  
  
 [CorDebugStateChange 列挙型](../../../../docs/framework/unmanaged-api/debugging/cordebugstatechange-enumeration.md)  
 プロセスへの変更に基づいて破棄が必要となった、キャッシュされたデータの量を示します。  
  
 CorDebugStepReason  
 個々のステップの結果を示します。  
  
 CorDebugThreadState  
 デバッグのスレッドの状態を指定します。  
  
 \>CorDebugUnmappedStop  
 ステッパによるコード実行の停止をトリガーする可能性のあるマップ解除したコードの型を指定します。  
  
 CorDebugUserState  
 スレッドのユーザーの状態を示します。  
  
 [CorGCReferenceType 列挙型](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md)  
 ガベージ コレクトされる必要のあるオブジェクトのソースを識別します。  
  
 [ILCodeKind 列挙型](../../../../docs/framework/unmanaged-api/debugging/ilcodekind-enumeration.md)  
 デバッガーがローカル変数またはプロファイラー ReJIT インストルメンテーションに追加されたコードにアクセスできるかどうかを指定する値を提供します。  
  
 [LoggingLevelEnum 列挙型](../../../../docs/framework/unmanaged-api/debugging/logginglevelenum-enumeration.md)  
 マネージ スレッドがイベントを記録する際にイベント ログに書き込まれる説明メッセージの重大度レベルを示します。  
  
 [LogSwitchCallReason 列挙型](../../../../docs/framework/unmanaged-api/debugging/logswitchcallreason-enumeration.md)  
 デバッグとトレースの切り替えで実行された操作を示します。  
  
 [VariableLocationType 列挙型](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 変数のネイティブの場所の種類を示します。  
  
 [WriteableMetadataUpdateMode 列挙型](../../../../docs/framework/unmanaged-api/debugging/writeablemetadataupdatemode-enumeration.md)  
 メモリ内のメタデータ更新をデバッガーに対して可視にするかどうかを指定する値を提供します。  
  
## <a name="related-sections"></a>関連項目  
 [デバッグ コクラス](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [デバッグ インターフェイス](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
  
 [デバッグ構造体](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
