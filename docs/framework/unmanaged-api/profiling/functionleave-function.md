---
title: "FunctionLeave 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: FunctionLeave
api_location: mscorwks.dll
api_type: COM
f1_keywords: FunctionLeave
helpviewer_keywords: FunctionLeave function [.NET Framework profiling]
ms.assetid: 18e89f45-e068-426a-be16-9f53a4346860
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3368a97adf6ffceaa5ac56b7ffe16d6e2802437c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="functionleave-function"></a>FunctionLeave 関数
関数が呼び出し元に戻るには約ことをプロファイラーに通知します。  
  
> [!NOTE]
>  `FunctionLeave`関数は、.NET Framework 2.0 で推奨されなくなりました。 作業を続けますが、パフォーマンスの低下が発生します。 使用して、 [FunctionLeave2](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)関数を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionLeave (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcID`  
 [in]返す関数の識別子。  
  
## <a name="remarks"></a>コメント  
 `FunctionLeave`関数コールバックです。 これを実装する必要があります。 実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。  
  
 実装`FunctionLeave`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。 実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。 ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionLeave`を返します。  
  
 また、`FunctionLeave`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>関連項目  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [FunctionTailcall2 関数](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)  
 [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [プロファイリング グローバル静的関数](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
