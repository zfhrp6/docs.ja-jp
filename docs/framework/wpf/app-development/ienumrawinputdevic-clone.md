---
title: IEnumRAWINPUTDEVIC:Clone
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Clone method [WPF]
ms.assetid: 2a6a1900-aa55-45fa-9382-241d569a2dc4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 35f3c00f3a0efd41c425ba29f8465a73e78d624c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2017
---
# <a name="ienumrawinputdevicclone"></a>IEnumRAWINPUTDEVIC:Clone
同じリストを反復処理するため、現在の列挙子と同じ状態の別の未加工入力デバイスの列挙子を作成します。  
  
## <a name="syntax"></a>構文  
  
```  
HRESULT Clone( [out] IEnumRAWINPUTDEVICE **ppenum);  
```  
  
#### <a name="parameters"></a>パラメーター  
 `ppenum`  
  
 [out]受け取る出力変数のアドレス、 [IEnumRAWINPUTDEVICE](../../../../docs/framework/wpf/app-development/ienumrawinputdevice.md)インターフェイス ポインター。 メソッドが成功した場合は、この output 変数の値は定義されません。  
  
## <a name="property-valuereturn-value"></a>プロパティ値/戻り値  
 HRESULT: このメソッドは、E_INVALIDARG、E_UNEXPECTED、E_OUTOFMEMORY は、標準の戻り値をサポートします。  
  
## <a name="remarks"></a>コメント  
 このメソッドでは、後でそのポイントを返すために、列挙のシーケンスで、ポイントを録音することです。 呼び出し元は、最初の列挙子から個別に新しいこの列挙子を解放する必要があります。
