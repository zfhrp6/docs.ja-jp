---
title: ICorProfilerCallback::Shutdown メソッド
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 83e32b2b69d53772f8a4ebaabe1c025b95d1da47
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453728"
---
# <a name="icorprofilercallbackshutdown-method"></a>ICorProfilerCallback::Shutdown メソッド
アプリケーションがシャット ダウンしているプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a>コメント  
 プロファイラー コードがのメソッドを安全に呼び出すことはできません、 [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)インターフェイスの後に、`Shutdown`メソッドが呼び出されます。 呼び出しの`ICorProfilerInfo`メソッドの後に未定義の動作が発生、`Shutdown`メソッドを返します。 シャット ダウン後にこの特定の変更できないイベントがあります。プロファイラーは、これが発生するとすぐに戻ります注意する必要があります。  
  
 `Shutdown`プロファイリングされているマネージ アプリケーションがマネージ コードとして開始された場合のみ、メソッドが呼び出されます (つまり、プロセスのスタックの初期のフレームが管理対象)。 アプリケーションがアンマネージ コードとして開始された後でマネージ コードにジャンプする場合は、それによってインスタンスを作成する共通言語ランタイム (CLR) の`Shutdown`は呼び出されません。 このような場合、プロファイラーが、ライブラリに含める必要があります、`DllMain`ルーチン、ありますを使用する値の任意のリソースを解放し、トレースなどのディスクにフラッシュなど、そのデータのクリーンアップ処理を実行します。  
  
 一般に、プロファイラーは、予期しないシャット ダウンに対処する必要があります。 たとえば、win32 のプロセスを中止する可能性があります`TerminateProcess`メソッド (Winbase.h で宣言)。 それ以外の場合、CLR は、それらの計画的な破壊メッセージを配信せず特定のマネージ スレッド (バック グラウンド スレッド) を停止します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー** : CorProf.idl、CorProf.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [ICorProfilerCallback インターフェイス](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [Initialize メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)
