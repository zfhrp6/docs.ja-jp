---
title: _EFN_StackTrace 関数
ms.date: 03/30/2017
api_name:
- _EFN_StackTrace
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- _EFN_StackTrace
helpviewer_keywords:
- _EFN_StackTrace function [.NET Framework debugging]
ms.assetid: caea7754-867c-4360-a65c-5ced4408fd9d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 39a249108d10e5dc382775378e2d6b84bba87356
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33408087"
---
# <a name="efnstacktrace-function"></a>_EFN_StackTrace 関数
マネージ スタック トレースのテキスト表現および `CONTEXT` レコードの配列 (アンマネージ コードとマネージ コードの間の各移行につき 1 つ) を提供します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT CALLBACK _EFN_StackTrace(  
    [in]  PDEBUG_CLIENT  Client,  
    [out] WCHAR          wszTextOut[],  
    [out] size_t         *puiTextLength,  
    [out] LPVOID         pTransitionContexts,  
    [out] size_t         *puiTransitionContextCount,  
    [in]  size_t         uiSizeOfContext,  
    [in]  DWORD          Flags  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `Client`  
 [in]デバッグ中のクライアント。  
  
 `wszTextOut`  
 [out]スタック トレースのテキスト表現。  
  
 `puiTextLength`  
 [out]文字数へのポインター`wszTextOut`です。  
  
 `pTransitionContexts`  
 [out]遷移のコンテキストの配列です。  
  
 `puiTransitionContextCount`  
 [out]配列内の遷移のコンテキストの数へのポインター。  
  
 `uiSizeOfContext`  
 [in]Context 構造体のサイズ。  
  
 `Flags`  
 [in]0 または SOS_STACKTRACE_SHOWADDRESSES (0x01) のいずれかに設定する EBP レジスタとそれぞれの前に enter スタック ポインター (ESP) を表示`module!functionname`行です。  
  
## <a name="remarks"></a>コメント  
 `_EFN_StackTrace`構造体は、WinDbg プログラム インターフェイスから呼び出すことができます。 パラメーターは、次のように使用されます。  
  
-   場合`wszTextOut`が null と`puiTextLength`が null でない関数、文字列の長さを返しますで`puiTextLength`です。  
  
-   場合`wszTextOut`が null でない内のテキストは、関数には格納`wszTextOut`によって示される位置まで`puiTextLength`です。 バッファーの長さが不足している場合、バッファー、または返します E_OUTOFMEMORY で十分な空き領域が認識されたかどうかを正常に返します。  
  
-   場合、関数の遷移の部分は無視されます`pTransitionContexts`と`puiTransitionContextCount`が両方とも null です。 この場合、関数は、関数名のみのテキスト出力を持つ呼び出し元を提供します。  
  
-   場合`pTransitionContexts`が null と`puiTransitionContextCount`が null でない関数、必要なエントリ数を返しますのコンテキストで`puiTransitionContextCount`です。  
  
-   場合`pTransitionContexts`が null でない関数として扱われます長さの構造体の配列`puiTransitionContextCount`です。 構造体のサイズである`uiSizeOfContext`のサイズを指定する必要があります[SimpleContext](../../../../docs/framework/unmanaged-api/debugging/stacktrace-simplecontext-structure.md)または`CONTEXT`アーキテクチャに対応します。  
  
-   `wszTextOut` 次の形式で書き込まれます。  
  
    ```  
    "<ModuleName>!<Function Name>[+<offset in hex>]  
    ...  
    (TRANSITION)  
    ..."  
    ```  
  
-   16 進数でオフセットが「0x0」の場合、オフセットは書き込まれません。  
  
-   ない場合マネージ コードのスレッドで現在のコンテキストで、SOS_E_NOMANAGEDCODE を返します。  
  
-   `Flags`パラメーターが 0 または前にある各 EBP と ESP を表示する SOS_STACKTRACE_SHOWADDRESSES`module!functionname`行です。 既定では、これは 0 です。  
  
    ```  
    #define SOS_STACKTRACE_SHOWADDRESSES   0x00000001  
    ```  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** SOS_Stacktrace.h  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [デバッグ グローバル静的関数](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
