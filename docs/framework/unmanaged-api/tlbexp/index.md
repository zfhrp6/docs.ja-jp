---
title: "Tlbexp ヘルパー関数 (アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: d5d0a0b08be725a50442a3db9f9942bceea7cf8a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a>Tlbexp ヘルパー関数 (アンマネージ API リファレンス)
[タイプ ライブラリ エクスポーター ツール](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)(Tlbexp.exe) が TlbRef.dll をという名前のダイナミック リンク ライブラリを読み込みます。 この DLL には、2 つのヘルパー関数とエクスポーター ツールが、アセンブリをタイプ ライブラリへの変換処理中に使用するインターフェイスが含まれています。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [GetTypeLibInfo 関数](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 タイプ ライブラリのローカライズとオペレーティング システムの情報を提供します。  
  
 [LoadTypeLibWithResolver 関数](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 実装を使用して、タイプ ライブラリを読み込み、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)いずれかを解決するのには、タイプ ライブラリを参照します。  
  
 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 提供、 [ResolveTypeLib メソッド](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)、タイプ ライブラリの完全修飾パスが返されます。
