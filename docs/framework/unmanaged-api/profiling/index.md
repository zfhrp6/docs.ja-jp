---
title: プロファイル (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- profiling [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], profiling
- unmanaged API reference [.NET Framework], profiling
ms.assetid: 14c68e84-657e-49c2-aa8b-4978dbaf4454
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 581f42dc83622712dbb30ef556a481388bafe259
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33455573"
---
# <a name="profiling-unmanaged-api-reference"></a><span data-ttu-id="f7434-102">プロファイル (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="f7434-102">Profiling (Unmanaged API Reference)</span></span>
<span data-ttu-id="f7434-103">プロファイル API を使用すると、プロファイラーは、共通言語ランタイム (CLR) によってプログラムの実行を監視します。</span><span class="sxs-lookup"><span data-stu-id="f7434-103">The profiling API enables a profiler to monitor a program's execution by the common language runtime (CLR).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f7434-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="f7434-104">In This Section</span></span>  
 [<span data-ttu-id="f7434-105">プロファイルの概要</span><span class="sxs-lookup"><span data-stu-id="f7434-105">Profiling Overview</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-overview.md)  
 <span data-ttu-id="f7434-106">サービスと .NET Framework 環境でプロファイルをサポートするために、CLR が提供するインターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-106">Describes the services and interfaces that the CLR provides to support profiling in the .NET Framework environment.</span></span>  
  
 [<span data-ttu-id="f7434-107">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f7434-107">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 <span data-ttu-id="f7434-108">プロファイル API で使用されるアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-108">Describes the unmanaged interfaces that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="f7434-109">プロファイル環境の設定</span><span class="sxs-lookup"><span data-stu-id="f7434-109">Setting Up a Profiling Environment</span></span>](../../../../docs/framework/unmanaged-api/profiling/setting-up-a-profiling-environment.md)  
 <span data-ttu-id="f7434-110">.NET Framework アプリケーションのプロファイリングを行う手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-110">Describes the steps you must take to profile a .NET Framework application.</span></span>  
  
 [<span data-ttu-id="f7434-111">CLR プロファイラと Windows ストア アプリ</span><span class="sxs-lookup"><span data-stu-id="f7434-111">CLR Profilers and Windows Store Apps</span></span>](../../../../docs/framework/unmanaged-api/profiling/clr-profilers-and-windows-store-apps.md)  
 <span data-ttu-id="f7434-112">正常に機能する Windows ストア アプリを使用して CLR プロファイル API を使用する診断ツールを移植する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-112">Discusses how to port diagnostic tools that consume the CLR Profiling API to work successfully with Windows Store apps.</span></span>  
  
 [<span data-ttu-id="f7434-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span><span class="sxs-lookup"><span data-stu-id="f7434-113">CORPROF_E_UNSUPPORTED_CALL_SEQUENCE HRESULT</span></span>](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md)  
 <span data-ttu-id="f7434-114">文書化されるメソッドの呼び出しが返された条件、 `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT。</span><span class="sxs-lookup"><span data-stu-id="f7434-114">Documents the conditions under which a method call returns the `CORPROF_E_UNSUPPORTED_CALL_SEQUENCE` HRESULT.</span></span>  
  
 [<span data-ttu-id="f7434-115">グローバル静的関数のプロファイル</span><span class="sxs-lookup"><span data-stu-id="f7434-115">Profiling Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-global-static-functions.md)  
 <span data-ttu-id="f7434-116">プロファイル API で使用されるアンマネージ グローバル静的関数について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-116">Describes the unmanaged global static functions that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="f7434-117">列挙型のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f7434-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)  
 <span data-ttu-id="f7434-118">プロファイル API で使用されるアンマネージ列挙体について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-118">Describes the unmanaged enumerations that the profiling API uses.</span></span>  
  
 [<span data-ttu-id="f7434-119">構造体のプロファイリング</span><span class="sxs-lookup"><span data-stu-id="f7434-119">Profiling Structures</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-structures.md)  
 <span data-ttu-id="f7434-120">プロファイル API で使用されるアンマネージ構造体について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-120">Describes the unmanaged structures that the profiling API uses.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="f7434-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="f7434-121">Related Sections</span></span>  
 [<span data-ttu-id="f7434-122">チュートリアル: パフォーマンスの問題を特定する</span><span class="sxs-lookup"><span data-stu-id="f7434-122">Walkthrough: Identifying Performance Problems</span></span>](/visualstudio/profiling/walkthrough-identifying-performance-problems)  
 <span data-ttu-id="f7434-123">Microsoft Visual Studio 2005 Team System で組み込みのプロファイリング ツールを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="f7434-123">Explains how to use the built-in profiling tools in the Microsoft Visual Studio 2005 Team System.</span></span> <span data-ttu-id="f7434-124">これらのツールは、プロファイル API を使用して他の方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="f7434-124">These tools provide an alternative approach to using the profiling API.</span></span>
