---
title: "ISymUnmanagedWriter::GetDebugInfo メソッド"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedWriter.GetDebugInfo
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedWriter::GetDebugInfo
helpviewer_keywords:
- ISymUnmanagedWriter::GetDebugInfo method [.NET Framework debugging]
- GetDebugInfo method [.NET Framework debugging]
ms.assetid: dd31c210-6829-45eb-927e-cc53932638b7
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 562e9015f2aa402a90a7b31e4b7002e68893a812
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedwritergetdebuginfo-method"></a>ISymUnmanagedWriter::GetDebugInfo メソッド
ポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリ エントリを書き込むときにコンパイラに必要な情報を返します。 シンボル ライターを除くのすべてのフィールドは`TimeDateStamp`と`PointerToRawData`です。 (コンパイラ、これら 2 つのフィールドを適切に設定します。)  
  
 このメソッドを呼び出す、PE ファイルにデータの blob を出力、設定する必要があります、コンパイラ、 `PointerToRawData` IMAGE_DEBUG_DIRECTORY、出力されたデータをポイントして、IMAGE_DEBUG_DIRECTORY を PE ファイルに書き込むフィールド。 コンパイラを設定する必要がありますも、`TimeDateStamp`と一致するフィールド、 `TimeDateStamp` PE ファイルが生成されるのです。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT GetDebugInfo(  
    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,  
    [in]  DWORD cData,  
    [out] DWORD *pcData,  
    [out, size_is(cData),  
        length_is(*pcData)] BYTE data[]);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `pIDD`  
 [入力、出力].シンボルのライターが入力する IMAGE_DEBUG_DIRECTORY へのポインター。  
  
 `cData`  
 [in]A`DWORD`デバッグ データのサイズを格納します。  
  
 `pcData`  
 [out]ポインター、`DWORD`デバッグ データの格納に必要なバッファーのサイズを受け取る。  
  
 `data`  
 [out]シンボル ストアのデバッグ データを保持するのに十分な大きさであるバッファーへのポインター。  
  
## <a name="return-value"></a>戻り値  
 メソッドが成功した場合は S_OK、それ以外の場合、E_FAIL またはその他のエラー コード。  
  
## <a name="requirements"></a>要件  
 **ヘッダー:** CorSym.idl、CorSym.h  
  
## <a name="see-also"></a>関連項目  
 [ISymUnmanagedWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
