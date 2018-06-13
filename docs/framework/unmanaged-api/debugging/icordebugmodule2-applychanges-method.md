---
title: ICorDebugModule2::ApplyChanges メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ApplyChanges
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ApplyChanges
helpviewer_keywords:
- ApplyChanges method [.NET Framework debugging]
- ICorDebugModule2::ApplyChanges method [.NET Framework debugging]
ms.assetid: 96fa3406-6a6f-41a1-88c6-d9bc5d1a16d1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a406e945a67352bc7f126b40bd56f4a11dd693b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419544"
---
# <a name="icordebugmodule2applychanges-method"></a>ICorDebugModule2::ApplyChanges メソッド
実行中のプロセスにメタデータの変更と Microsoft intermediate language (MSIL) コードの変更を適用します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT ApplyChanges (  
    [in] ULONG                       cbMetadata,  
    [in, size_is(cbMetadata)] BYTE   pbMetadata[],  
    [in] ULONG                       cbIL,  
    [in, size_is(cbIL)] BYTE         pbIL[]  
);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `cbMetadata`  
 [in]デルタ メタデータのバイト単位のサイズ。  
  
 `pbMetadata`  
 [in]デルタのメタデータを格納するバッファー。 バッファーのアドレスから返される、 [imetadataemit 2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md)メソッドです。  
  
 メタデータ内の相対仮想アドレス (Rva) は、MSIL コードの先頭からの相対にする必要があります。  
  
 `cbIL`  
 [in]デルタ MSIL コードのバイト単位のサイズ。  
  
 `pbIL`  
 [in]更新された MSIL コードを格納するバッファー。  
  
## <a name="remarks"></a>コメント  
 `pbMetadata`パラメーター形式では、特別なデルタ メタデータ (によって出力として[imetadataemit 2::savedeltatomemory](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-savedeltatomemory-method.md))。 `pbMetadata` ベースとして前のメタデータを取得し、そのベースに適用する個々 の変更点について説明します。  
  
 これに対し、 `pbIL[`] パラメーターは、新しい、更新されたメソッドの MSIL が含まれており、そのメソッドの以前の MSIL を完全に置き換えることを意図しました。  
  
 デバッガーのメモリ内で、デルタ MSIL とメタデータが作成されているときに、デバッガーが呼び出す`ApplyChanges`共通言語ランタイム (CLR) に変更を送信します。 ランタイムは、そのメタデータ テーブルを更新、新しい MSIL をプロセスに配置し、新しい MSIL の・ イン タイム (JIT) コンパイルを設定します。 変更が適用されて、デバッガーで呼び出す必要があります[imetadataemit 2::resetenclog](../../../../docs/framework/unmanaged-api/metadata/imetadataemit2-resetenclog-method.md) [次へ] の編集セッションの準備をします。 デバッガーは、プロセスを続行することもできます。  
  
 デバッガーが呼び出すたびに`ApplyChanges`デルタ メタデータが含まれているモジュールに呼び出す必要もあります[imetadataemit::applyeditandcontinue](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-applyeditandcontinue-method.md)すべてのコピーを除くそのモジュールのメタデータのコピーを同じデルタ メタデータを持つ変更内容を出力するために使用します。 場合は、メタデータのコピーでは、非同期のしなくなると実際のメタデータとデバッガー常にそのコピーを破棄して新しいコピーを入手します。  
  
 場合、`ApplyChanges`メソッドが失敗した場合は、デバッグ セッションは無効な状態および再起動する必要があります。  
  
## <a name="requirements"></a>要件  
 **プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。  
  
 **ヘッダー:** CorDebug.idl、CorDebug.h  
  
 **ライブラリ:** CorGuids.lib  
  
 **.NET framework のバージョン:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
