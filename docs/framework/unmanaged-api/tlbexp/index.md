---
title: Tlbexp ヘルパー関数 (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- exporter tool [.NET Framework]
- TlbRef.dll
- Tlbexp.exe
- Type Library Exporter
ms.assetid: 5c0a3d14-5f26-4267-94a9-82c30f8db09a
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f41a233e9b5338bdb0a324ff9af267a97821d4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455874"
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
