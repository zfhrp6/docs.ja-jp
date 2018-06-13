---
title: _CorValidateImage 関数
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 101271823f7b7877bb7f007588b6a164233e5b45
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33432378"
---
# <a name="corvalidateimage-function"></a>_CorValidateImage 関数
マネージ モジュール イメージを検証し、それらが読み込まれると、オペレーティング システム ローダーに通知します。  
  
## <a name="syntax"></a>構文  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ImageBase`  
 [in]として検証するイメージの開始位置を指すポインターはマネージ コードです。 イメージは、メモリに既に読み込まれている必要があります。  
  
 `FileName`  
 [in]イメージのファイル名。  
  
## <a name="return-value"></a>戻り値  
 この関数は、標準の値を返します`E_INVALIDARG`、 `E_OUTOFMEMORY`、 `E_UNEXPECTED`、および`E_FAIL`、だけでなく、次の値。  
  
|戻り値|説明|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|イメージが正しくありません。 この値は、HRESULT 0xC000007BL を持っています。|  
|`STATUS_SUCCESS`|イメージは有効です。 この値は、HRESULT 0x00000000L を持っています。|  
  
## <a name="remarks"></a>コメント  
 Windows XP およびそれ以降のバージョンでは、オペレーティング システム ローダーは、共通のオブジェクト ファイル coff ヘッダー内の COM 記述子ディレクトリ ビットを調べることによってマネージ モジュールをチェックします。 設定済みビットでは、マネージ モジュールを示します。 MsCorEE.dll と呼び出し読み込む場合は、ローダーがマネージ モジュールを検出`_CorValidateImage`、次の操作を実行します。  
  
-   イメージが有効なマネージ モジュールであることを確認します。  
  
-   共通言語ランタイム (CLR) のエントリ ポイントにイメージ内のエントリ ポイントを変更します。  
  
-   64 ビット バージョンの Windows でイメージを PE32 から pe 32 + 形式に変換することによってがメモリ内に変更されます。  
  
-   マネージ モジュール イメージが読み込まれるときに、ローダーに戻ります。  
  
 実行可能イメージは、オペレーティング システム ローダーし、呼び出し、 [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md)関数の実行可能ファイルで指定されたエントリ ポイントに関係なく、します。 ローダーの呼び出し、DLL アセンブリのイメージ、 [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)関数。  
  
 `_CorExeMain` または`_CorDllMain`は、次の操作を実行します。  
  
-   CLR を初期化します。  
  
-   アセンブリの CLR ヘッダーからマネージ エントリ ポイントを検索します。  
  
-   実行を開始します。  
  
 ローダーの呼び出し、 [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md)管理されているときに機能モジュール イメージがアンロードされます。 ただし、この関数に任意のアクションを実行しませんだけを返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Cor.h  
  
 **ライブラリ:** MsCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 [メタデータ グローバル静的関数](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
