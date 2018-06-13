---
title: FunctionTailcall3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall3WithInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall3WithInfo
helpviewer_keywords:
- FunctionTailcall3WithInfo function [.NET Framework profiling]
ms.assetid: 46380fcc-0198-43ae-a1f5-2d4939425886
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 076666f920a5a6fcac3b4b75bb23717751ae1438
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453503"
---
# <a name="functiontailcall3withinfo-function"></a>FunctionTailcall3WithInfo 関数
現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知しに渡すことができるハンドルを提供、 [icorprofilerinfo 3::getfunctiontailcall3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)を取得しますスタック フレーム。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionTailcall3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionIDOrClientID`  
 [in]Tail の呼び出しを行うには、現在実行中の関数の識別子。  
  
 `eltInfo`  
 [in] 特定のスタック フレームに関する情報を表す不透明ハンドル。 このハンドルは、渡されるコールバック中にのみ有効です。  
  
## <a name="remarks"></a>コメント  
 `FunctionTailcall3WithInfo`関数が呼び出され、により、プロファイラーを使用すると、プロファイラーに通知のコールバック メソッド、 [icorprofilerinfo 3::getfunctiontailcall3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctiontailcall3info-method.md)をスタック フレームを検査します。 スタック フレームの情報にアクセスする、`COR_PRF_ENABLE_FRAME_INFO`を設定するフラグを持っています。 プロファイラーは、使用、 [icorprofilerinfo::seteventmask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定し、使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3withinfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)を登録する、この関数の実装です。  
  
 `FunctionTailcall3WithInfo`関数コールバックです。 これを実装する必要があります。 実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。  
  
 実装`FunctionTailcall3WithInfo`をブロックしないでください、ガベージ コレクションが延期されます。 実装しないでください、ガベージ コレクション スタックはガベージ コレクションに適した状態ではない可能性があります。 ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionTailcall3WithInfo`を返します。  
  
 また、FunctionTailcall3WithInfo 関数がマネージ コードを呼び出していない、または任意の方法で管理されているメモリの割り当てが発生する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [FunctionTailcall3](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionEnter3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functiontailcall3-function.md)  
 [FunctionLeave3WithInfo](../../../../docs/framework/unmanaged-api/profiling/functionleave3withinfo-function.md)  
 [SetEnterLeaveFunctionHooks3](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3-method.md)  
 [SetEnterLeaveFunctionHooks3WithInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)  
 [SetFunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-setfunctionidmapper-method.md)  
 [SetFunctionIDMapper2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setfunctionidmapper2-method.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
