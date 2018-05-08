---
title: FunctionTailcall2 関数
ms.date: 03/30/2017
api_name:
- FunctionTailcall2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall2
helpviewer_keywords:
- FunctionTailcall2 function [.NET Framework profiling]
ms.assetid: 249f9892-b5a9-41e1-b329-28a925904df6
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7a515c2622f81c666523aa012fa1e34e5251c074
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="functiontailcall2-function"></a>FunctionTailcall2 関数
現在実行中の関数は、別の関数の末尾呼び出しを実行する直前と、スタック フレームに関する情報を提供をプロファイラーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionTailcall2 (  
    [in] FunctionID         funcId,   
    [in] UINT_PTR           clientData,   
    [in] COR_PRF_FRAME_INFO func  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcId`  
 [in]Tail の呼び出しを行うには、現在実行中の関数の識別子。  
  
 `clientData`  
 [in]使用して、プロファイラーが指定されていたかを再割り当て関数識別子[FunctionIDMapper](../../../../docs/framework/unmanaged-api/profiling/functionidmapper-function.md)tail の呼び出しを行うには、現在実行中の関数。  
  
 `func`  
 [in]A`COR_PRF_FRAME_INFO`スタック フレームに関する情報を示す値。  
  
 プロファイラーはこれを不透明なハンドルでの実行エンジンに渡すことができるとして扱う必要があります、 [icorprofilerinfo 2::getfunctioninfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getfunctioninfo2-method.md)メソッドです。  
  
## <a name="remarks"></a>コメント  
 末尾呼び出しの対象の関数は、現在のスタック フレームが使用され、直接 tail の呼び出しを行った関数の呼び出し元に戻ります。 つまり、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)末尾呼び出しの対象となっている関数のコールバックは発行されません。  
  
 値、`func`パラメーターが後に無効、`FunctionTailcall2`値が変わる可能性があるか、破棄されるので、返されます。  
  
 `FunctionTailcall2`関数コールバックです。 これを実装する必要があります。 実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。  
  
 実装`FunctionTailcall2`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。 実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。 ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionTailcall2`を返します。  
  
 また、`FunctionTailcall2`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
