---
title: GetCORSystemDirectory 関数
ms.date: 03/30/2017
api_name:
- GetCORSystemDirectory
api_location:
- mscoree.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- GetCORSystemDirectory
helpviewer_keywords:
- GetCORSystemDirectory function [.NET Framework hosting]
ms.assetid: 3dcd16a7-dafc-4ca8-b5cd-20ffb37db91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 008514e3637a980f3722d0c9896a17be33d54c31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431689"
---
# <a name="getcorsystemdirectory-function"></a>GetCORSystemDirectory 関数
プロセスに読み込まれる共通言語ランタイム (CLR) のインストール ディレクトリを返します。 完全修飾のインストール ディレクトリはたとえば、"c:\windows\microsoft.net\framework\v1.0.3705"です。  
  
 この関数は推奨されません。 によって置き換えられた、 [iclrruntimeinfo::getruntimedirectory](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getruntimedirectory-method.md)で提供されるメソッド、[!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)]です。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetCORSystemDirectory (   
    [out] LPWSTR  pbuffer,     
    [in]  DWORD   cchBuffer,   
    [out] DWORD*  dwlength  
);   
```  
  
#### <a name="parameters"></a>パラメーター  
 `pbuffer`  
 [out]ランタイムが、プロセスに読み込まれたランタイムのインストール ディレクトリの完全修飾名を表す文字列を返すにバッファーです。 ランタイムがプロセスにまだ読み込まれていない場合は、コンピューターにインストールされているランタイムの最新バージョンの適切なディレクトリ情報を返します。  
  
 `cchBuffer`  
 [in]サイズをバイト単位での`pbuffer`します。  
  
 `dwLength`  
 [out]返される文字数`pbuffer`です。  
  
## <a name="remarks"></a>コメント  
  
> [!CAUTION]
>  CLR の version 4 を実行しているプロセスでは、この関数は使用しないでください。 CLR の以前のバージョンがコンピューターにインストールされている場合、この関数は、そのバージョンのインストール ディレクトリを返します。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** MSCorEE.h  
  
 **ライブラリ:** MSCorEE.dll  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>関連項目  
 
  [非推奨の CLR ホスト関数](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
