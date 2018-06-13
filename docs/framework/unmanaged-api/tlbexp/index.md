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
# <a name="tlbexp-helper-functions-unmanaged-api-reference"></a><span data-ttu-id="bf49d-102">Tlbexp ヘルパー関数 (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="bf49d-102">Tlbexp Helper Functions (Unmanaged API Reference)</span></span>
<span data-ttu-id="bf49d-103">[タイプ ライブラリ エクスポーター ツール](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md)(Tlbexp.exe) が TlbRef.dll をという名前のダイナミック リンク ライブラリを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="bf49d-103">The [Type Library Exporter tool](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) (Tlbexp.exe) loads a dynamic link library named TlbRef.dll.</span></span> <span data-ttu-id="bf49d-104">この DLL には、2 つのヘルパー関数とエクスポーター ツールが、アセンブリをタイプ ライブラリへの変換処理中に使用するインターフェイスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="bf49d-104">This DLL contains two helper functions and an interface that the exporter tool uses during the assembly-to-type-library conversion process.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bf49d-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="bf49d-105">In This Section</span></span>  
 [<span data-ttu-id="bf49d-106">GetTypeLibInfo 関数</span><span class="sxs-lookup"><span data-stu-id="bf49d-106">GetTypeLibInfo Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/gettypelibinfo-function.md)  
 <span data-ttu-id="bf49d-107">タイプ ライブラリのローカライズとオペレーティング システムの情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="bf49d-107">Provides localization and operating system information for a type library.</span></span>  
  
 [<span data-ttu-id="bf49d-108">LoadTypeLibWithResolver 関数</span><span class="sxs-lookup"><span data-stu-id="bf49d-108">LoadTypeLibWithResolver Function</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/loadtypelibwithresolver-function.md)  
 <span data-ttu-id="bf49d-109">実装を使用して、タイプ ライブラリを読み込み、 [ITypeLibResolver インターフェイス](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)いずれかを解決するのには、タイプ ライブラリを参照します。</span><span class="sxs-lookup"><span data-stu-id="bf49d-109">Loads a type library by using an implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any referenced type libraries.</span></span>  
  
 [<span data-ttu-id="bf49d-110">ITypeLibResolver インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bf49d-110">ITypeLibResolver Interface</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md)  
 <span data-ttu-id="bf49d-111">提供、 [ResolveTypeLib メソッド](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md)、タイプ ライブラリの完全修飾パスが返されます。</span><span class="sxs-lookup"><span data-stu-id="bf49d-111">Provides the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md), which returns the fully qualified path of a type library.</span></span>
