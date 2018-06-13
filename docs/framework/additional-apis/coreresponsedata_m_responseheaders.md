---
title: CoreResponseData.m_ResponseHeaders フィールド
ms.date: 01/29/2018
topic_type:
- apiref
api_name:
- System.Net.CoreResponseData.m_ResponseHeaders
api_location:
- System.dll
api_type:
- Assembly
author: stevewhims
ms.openlocfilehash: ea93b70ae8e1a710b4208050d7ec823a28b218b7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753665"
---
# <a name="coreresponsedatamresponseheaders-field"></a>CoreResponseData.m\_ResponseHeaders フィールド

`CoreResponseData.m_ResponseHeaders` <xref:System.Net.WebHeaderCollection>のサーバーの応答に関連付けられたヘッダー。

## <a name="syntax"></a>構文
  
```csharp
public WebHeaderCollection m_ResponseHeaders
```

> [!WARNING]
> この API は、コード内で直接使用するものではありません。 代わりに、使用する必要があります、<xref:System.Diagnostics.DiagnosticSource>ネットワーク用のコードをフックします。 参照してください[DiagnosticSource ユーザーズ ガイド 』](https://github.com/dotnet/corefx/blob/master/src/System.Diagnostics.DiagnosticSource/src/DiagnosticSourceUsersGuide.md)です。
> 
> Microsoft は、どのような状況下で、実稼働アプリケーションでこのクラスの使用をサポートしていません。

## <a name="requirements"></a>要件

**Namespace:** <xref:System.Net>

**アセンブリ:** システム (System.dll)

**.NET framework のバージョン:** 2.0 から利用可能です。
