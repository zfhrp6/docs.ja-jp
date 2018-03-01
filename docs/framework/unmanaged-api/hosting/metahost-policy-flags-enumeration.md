---
title: "METAHOST_POLICY_FLAGS 列挙体"
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
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a>METAHOST_POLICY_FLAGS 列挙体
ほとんどのランタイム ホストに共通するバインディング ポリシーを提供します。 この列挙体を使って、 [iclrmetahostpolicy::getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)メソッドです。  
  
## <a name="syntax"></a>構文  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a>メンバー  
  
|メンバー|説明|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|共通言語ランタイム (CLR) は、現在のプロセスに読み込まれると見なしません、高いレベルの互換性ポリシーを定義します。 代わりに、見なしますインストール済みの Clr のみと、コンポーネントの基本設定アセンブリ ファイル自体、宣言されたビルド対象のバージョン、または構成ファイルから派生したとして。|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|厳密な一致が見つからない場合に、HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft の内容に基づいて、バージョン バインドの結果にアップグレード ポリシーを適用\\です。NETFramework\Policy\Upgrades です。 同じ効果が[RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md)です。|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|呼び出しに提供されたイメージは、新しいプロセスで起動された場合と、バインディングの結果が返されます。 現在、`GetRequestedRuntime`読み込み可能なランタイムのセットを無視し、インストールされているランタイムのセットに対してバインドします。 このフラグを起動するときに、EXE がバインドするランタイムを決定するホストを使用します。|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|エラー ダイアログ ボックスが表示されます`GetRequestedRuntime`の入力パラメーターに互換性のあるランタイムを検索することはありません。 以降で、 [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]、このエラー ダイアログ ボックスは、ユーザーを該当する機能を有効にするかどうかを確認する Windows 機能 ダイアログ ボックスの形式を取ることができます。|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`バインディング プロセスに追加の入力としてプロセス イメージ (および対応する構成ファイル) を使用します。 既定では、`GetRequestedRuntime`に切り替えられないプロセス イメージのパス (通常は、プロセスを起動するために使用された EXE) に、ランタイムにバインドを決定する際にします。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`情報が、現在の構成ファイルでない場合に適切な SKU がインストールされているかどうかを確認する必要があります。 これにより、.NET Framework の既定のインストールよりも小さな Sku に正常に失敗する構成ファイルがないアプリケーション。 既定では、 `GetRequestedRuntime` SKU 属性が、構成ファイルで指定されていない限り、適切な SKU がインストールされているかどうかをチェックしません`<supportedRuntime />`要素。|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`情報が、現在の構成ファイルでない場合に適切な SKU がインストールされているかどうかを確認する必要があります。 これにより、.NET Framework の既定のインストールよりも小さな Sku に正常に失敗する構成ファイルがないアプリケーション。 既定では、 `GetRequestedRuntime` SKU 属性が、構成ファイルで指定されていない限り、適切な SKU がインストールされているかどうかをチェックしません`<supportedRuntime />`要素。|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`SEM_FAILCRITICALERRORS を無視する (呼び出すことによって設定される、 [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242)関数)、し、[エラー] ダイアログ ボックスを表示します。 既定では、SEM_FAILCRITICALERRORS は、[エラー] ダイアログ ボックスを抑制します。 別のプロセスから継承されているし、サイレントのエラーが、シナリオでは望ましくない可能性があります。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="requirements"></a>必要条件  
 **プラットフォーム:**を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** Metahost.h  
  
 **ライブラリ:** MSCorEE.dll にリソースとして含まれています。  
  
 **.NET framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>参照  
 [ホスティングの列挙型](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [GetRequestedRuntime メソッド](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
