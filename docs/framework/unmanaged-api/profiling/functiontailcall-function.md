---
title: "FunctionTailcall 関数"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- FunctionTailcall
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- FunctionTailcall
helpviewer_keywords:
- FunctionTailcall function [.NET Framework profiling]
ms.assetid: 66347e03-9a97-41e8-8f9d-89b80803f7b5
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 223f112ba405e29b800456adca2f83e0cef6e7b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="functiontailcall-function"></a>FunctionTailcall 関数
現在実行中の関数は、別の関数の末尾呼び出しを実行しようとして、プロファイラーに通知します。  
  
> [!NOTE]
>  `FunctionTailcall`関数は、.NET Framework version 2.0 で推奨されなくなりました。 作業を続けますが、パフォーマンスの低下が発生します。 使用して、 [FunctionTailcall2](../../../../docs/framework/unmanaged-api/profiling/functiontailcall2-function.md)関数を使用します。  
  
## <a name="syntax"></a>構文  
  
```  
void __stdcall FunctionTailcall (  
    [in] FunctionID funcID  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `funcID`  
 [in]Tail の呼び出しを行うには、現在実行中の関数の識別子。  
  
## <a name="remarks"></a>コメント  
 末尾呼び出しの対象の関数は、現在のスタック フレームが使用され、直接 tail の呼び出しを行った関数の呼び出し元に戻ります。 つまり、 [FunctionLeave](../../../../docs/framework/unmanaged-api/profiling/functionleave-function.md)末尾呼び出しの対象となっている関数のコールバックは発行されません。  
  
 `FunctionTailcall`関数コールバックです。 これを実装する必要があります。 実装を使用する必要があります、 `__declspec`(`naked`) ストレージ クラス属性。  
  
 実行エンジンは、この関数を呼び出す前に、レジスタを保存できません。  
  
-   エントリを上には、浮動小数点ユニット (FPU) にあるなど、使用するすべてのレジスタを保存する必要があります。  
  
-   終了時に、その呼び出し元がプッシュされたすべてのパラメーターをポップすることで、スタックを復元する必要があります。  
  
 実装`FunctionTailcall`ガベージ コレクションを遅らせることがあるためにをブロックしないでください。 実装は、ガベージ コレクションをしないでスタックはガベージ コレクションに適した状態ではない可能性があります。 ガベージ コレクションが実行されると、ランタイムがまでブロックされます`FunctionTailcall`を返します。  
  
 また、`FunctionTailcall`関数を呼び出してはならないようにまたはマネージ コードにマネージ メモリの割り当て。  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorProf.idl  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** 1.1、1.0  
  
## <a name="see-also"></a>参照  
 [FunctionEnter2 関数](../../../../docs/framework/unmanaged-api/profiling/functionenter2-function.md)  
 [FunctionLeave2 関数](../../../../docs/framework/unmanaged-api/profiling/functionleave2-function.md)  
 [SetEnterLeaveFunctionHooks2 メソッド](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-setenterleavefunctionhooks2-method.md)  
 [グローバル静的関数のプロファイル](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)
