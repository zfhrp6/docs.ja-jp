---
title: _CorDllMain 関数
ms.date: 03/30/2017
api_name:
- _CorDllMain
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorDllMain
helpviewer_keywords:
- _CorDllMain function [.NET Framework hosting]
ms.assetid: bc7b51cf-39d3-48ec-a5cb-2f179fbefff8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5d541f834e829305fa2b091c45d0dc8f387bb55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431671"
---
# <a name="cordllmain-function"></a>_CorDllMain 関数
共通言語ランタイム (CLR) を初期化、DLL アセンブリの CLR ヘッダーでマネージ エントリ ポイントを検索および実行を開始します。  
  
## <a name="syntax"></a>構文  
  
```  
BOOL STDMETHODCALLTYPE _CorDllMain (  
   [in] HINSTANCE hInst,  
   [in] DWORD     dwReason,  
   [in] LPVOID    lpReserved  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `hInst`  
 [in]読み込まれたモジュールのインスタンス ハンドル。  
  
 `dwReason`  
 [in]DLL エントリ ポイント関数が呼び出される理由を示します。 このパラメーターは、次の値のいずれかを指定できます: DLL_PROCESS_ATTACH、DLL_THREAD_ATTACH、DLL_THREAD_ATTACH、またはあります。 これらの値の詳細については、次を参照してください。、`DllMain`プラットフォーム SDK のドキュメントです。  
  
 `lpReserved`  
 [in]使用しません。  
  
## <a name="return-value"></a>戻り値  
 このメソッドが戻る`true`の成功と`false`場合は、エラーが発生します。  
  
## <a name="remarks"></a>コメント  
 この関数は、DLL アセンブリのオペレーティング システム ローダーによって呼び出されます。 実行可能アセンブリ ローダーの呼び出し、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数を使用します。  
  
 オペレーティング システム ローダーでは、DLL のファイルで指定されたエントリ ポイントに関係なく、このメソッドを呼び出します。  
  
 Windows 98、Windows ME、Windows NT、および Windows 2000 で、`_CorDllMain`関数が直接呼び出されていない、fixupin を介してオペレーティング システム ローダー。 その他のすべてのバージョンの Windows では、オペレーティング システム ローダーによって直接呼び出されます。  
  
 詳細については、「解説」セクションを参照してください、 [_CorValidateImage](../../../../docs/framework/unmanaged-api/hosting/corvalidateimage-function.md)トピックです。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
