---
title: "COM 相互運用の例外の処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: error-reference
helpviewer_keywords:
- unmanaged code, exceptions
- exceptions, unmanaged code
- HRESULTs
- exceptions, COM interop
- COM interop, exceptions
ms.assetid: e6104aa8-8e5f-4069-b864-def85579c96c
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e894d07e77b929b1ea22df2d34e542544ec3b1f3
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/23/2017
---
# <a name="handling-com-interop-exceptions"></a>COM 相互運用の例外の処理
マネージ コードとアンマネージ コードは、例外を処理するために一緒に操作できます。 マネージ コードでメソッドが例外をスローすると、共通言語ランタイムは、HRESULT を COM オブジェクトに渡すことができます。 アンマネージ コードでメソッドが失敗して、失敗を示す HRESULT を返した場合、ランタイムはマネージ コードでキャッチできる例外をスローします。  
  
 ランタイムは、HRESULT を COM 相互運用からの自動的にマップして、より詳細な例外を取得します。 たとえば、E_ACCESSDENIED は <xref:System.UnauthorizedAccessException> になり、E_OUTOFMEMORY は <xref:System.OutOfMemoryException> になるなどです。  
  
 HRESULT がカスタムの結果であるか、またはランタイムで不明な場合は、ランタイムがジェネリック <xref:System.Runtime.InteropServices.COMException> をクライアントに渡します。 **COMException** の **ErrorCode** プロパティには、HRESULT 値が含まれます。  
  
## <a name="working-with-ierrorinfo"></a>IErrorInfo の処理  
 エラーが COM からマネージ コードに渡された場合、ランタイムは例外オブジェクトにエラー情報を入れます。 IErrorInfo をサポートして HRESULT を返す COM オブジェクトは、この情報をマネージ コードの例外に提供します。 たとえば、ランタイムは、COM エラーからの説明を例外の <xref:System.Exception.Message%2A> プロパティにマップします。 HRESULT が追加のエラー情報を提供しない場合、ランタイムは例外のプロパティの多くに既定値を指定します。  
  
 アンマネージ コードでメソッドが失敗した場合、例外をマネージ コードのセグメントに渡すことができます。 「[HRESULT と例外](../../../docs/framework/interop/how-to-map-hresults-and-exceptions.md)」のトピックには、HRESULT がランタイム例外オブジェクトにマップする方法を示す表が含まれています。  

## <a name="see-also"></a>参照
[例外](index.md) 
