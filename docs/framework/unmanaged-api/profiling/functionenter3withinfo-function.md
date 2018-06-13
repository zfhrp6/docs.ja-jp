---
title: FunctionEnter3WithInfo 関数
ms.date: 03/30/2017
api_name:
- FunctionEnter3WithInfo
api_location:
- mscorwks.cll
api_type:
- COM
f1_keywords:
- FunctionEnter3WithInfo
helpviewer_keywords:
- FunctionEnter3WithInfo function [.NET Framework profiling]
ms.assetid: 277c3344-d0cb-431e-beae-eb1eeeba8eea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6a36f9b54ce7ac6a0a5a22b33a4d07150a96f40b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33452544"
---
# <a name="functionenter3withinfo-function"></a>FunctionEnter3WithInfo 関数
コントロールが、関数に渡されることをプロファイラーに通知しに渡すことができるハンドルを提供、 [icorprofilerinfo 3::getfunctionenter3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)スタック フレームと関数の引数を取得します。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionEnter3WithInfo(  
               [in] FunctionIDOrClientID functionIDOrClientID,  
               [in] COR_PRF_ELT_INFO eltInfo);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `functionIDOrClientID`  
 [in]制御が渡されます関数の識別子。  
  
 `eltInfo`  
 [in] 特定のスタック フレームに関する情報を表す不透明ハンドル。 このハンドルは、渡されるコールバック中にのみ有効です。  
  
## <a name="remarks"></a>コメント  
 `FunctionEnter3WithInfo`関数が呼び出され、により、プロファイラーを使用すると、プロファイラーに通知のコールバック メソッド、 [icorprofilerinfo 3::getfunctionenter3info メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)を引数の値を検査します。 引数の情報にアクセスする、`COR_PRF_ENABLE_FUNCTION_ARGS`を設定するフラグを持っています。 プロファイラーは、使用、 [icorprofilerinfo::seteventmask メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-seteventmask-method.md)イベント フラグを設定し、使用して、 [icorprofilerinfo 3::setenterleavefunctionhooks3withinfo メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-setenterleavefunctionhooks3withinfo-method.md)を登録する、この関数の実装です。  
  
 `FunctionEnter3WithInfo`関数コールバックです。 これを実装する必要があります。 実装を使用する必要があります、`__declspec(naked)`ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。  
  
 実装`FunctionEnter3WithInfo`をブロックしないでください、ガベージ コレクションが延期されます。 実装しないでください、ガベージ コレクション スタックはガベージ コレクションに適した状態ではない可能性があります。 ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionEnter3WithInfo`を返します。  
  
 `FunctionEnter3WithInfo`関数がマネージ コードを呼び出していない、または任意の方法で管理されているメモリの割り当てが発生する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [GetFunctionEnter3Info](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getfunctionenter3info-method.md)  
 [FunctionEnter3](../../../../docs/framework/unmanaged-api/profiling/functionenter3-function.md)  
 [FunctionLeave3](../../../../docs/framework/unmanaged-api/profiling/functionleave3-function.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
