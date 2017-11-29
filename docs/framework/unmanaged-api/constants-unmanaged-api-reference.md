---
title: "定数 (アンマネージ API リファレンス)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- constants for unmanaged API [.NET Framework]
- native API reference [.NET Framework], constants
- unmanaged API reference [.NET Framework], constants
ms.assetid: 77526f65-b71c-4483-9d19-3a3751fd8a45
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 45e4d41c16695010dc452d2f22850d43f885974a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="constants-unmanaged-api-reference"></a><span data-ttu-id="7c867-102">定数 (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="7c867-102">Constants (Unmanaged API Reference)</span></span>
<span data-ttu-id="7c867-103">このトピックでは、言語の種類、言語の販売元、および CorSym.idl で定義されているドキュメント型の定数について説明します。</span><span class="sxs-lookup"><span data-stu-id="7c867-103">This topic describes the language type, language vendor, and document type constants that are defined in CorSym.idl.</span></span>  
  
## <a name="language-type-constants"></a><span data-ttu-id="7c867-104">言語型定数</span><span class="sxs-lookup"><span data-stu-id="7c867-104">Language Type Constants</span></span>  
 <span data-ttu-id="7c867-105">次の表は、プログラミング言語を識別する Guid を表す型定数は、言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-105">The following table shows language type constants, which represent GUIDs that identify programming languages.</span></span>  
  
|<span data-ttu-id="7c867-106">シンボル</span><span class="sxs-lookup"><span data-stu-id="7c867-106">Symbol</span></span>|<span data-ttu-id="7c867-107">説明</span><span class="sxs-lookup"><span data-stu-id="7c867-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c867-108">CorSym_LanguageType_C</span><span class="sxs-lookup"><span data-stu-id="7c867-108">CorSym_LanguageType_C</span></span>|<span data-ttu-id="7c867-109">C 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-109">Indicates the C language.</span></span>|  
|<span data-ttu-id="7c867-110">CorSym_LanguageType_CPlusPlus</span><span class="sxs-lookup"><span data-stu-id="7c867-110">CorSym_LanguageType_CPlusPlus</span></span>|<span data-ttu-id="7c867-111">C++ 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-111">Indicates the C++ language.</span></span>|  
|<span data-ttu-id="7c867-112">CorSym_LanguageType_CSharp</span><span class="sxs-lookup"><span data-stu-id="7c867-112">CorSym_LanguageType_CSharp</span></span>|<span data-ttu-id="7c867-113">C# 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-113">Indicates the C# language.</span></span>|  
|<span data-ttu-id="7c867-114">CorSym_LanguageType_Basic</span><span class="sxs-lookup"><span data-stu-id="7c867-114">CorSym_LanguageType_Basic</span></span>|<span data-ttu-id="7c867-115">基本的な言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-115">Indicates the Basic language.</span></span>|  
|<span data-ttu-id="7c867-116">CorSym_LanguageType_Java</span><span class="sxs-lookup"><span data-stu-id="7c867-116">CorSym_LanguageType_Java</span></span>|<span data-ttu-id="7c867-117">Java 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-117">Indicates the Java language.</span></span>|  
|<span data-ttu-id="7c867-118">CorSym_LanguageType_Cobol</span><span class="sxs-lookup"><span data-stu-id="7c867-118">CorSym_LanguageType_Cobol</span></span>|<span data-ttu-id="7c867-119">COBOL 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-119">Indicates the COBOL language.</span></span>|  
|<span data-ttu-id="7c867-120">CorSym_LanguageType_Pascal</span><span class="sxs-lookup"><span data-stu-id="7c867-120">CorSym_LanguageType_Pascal</span></span>|<span data-ttu-id="7c867-121">Pascal 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-121">Indicates the Pascal language.</span></span>|  
|<span data-ttu-id="7c867-122">CorSym_LanguageType_ILAssembly</span><span class="sxs-lookup"><span data-stu-id="7c867-122">CorSym_LanguageType_ILAssembly</span></span>|<span data-ttu-id="7c867-123">Microsoft intermediate language (MSIL) のアセンブリのコードを示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-123">Indicates the Microsoft intermediate language (MSIL) assembly code.</span></span>|  
|<span data-ttu-id="7c867-124">CorSym_LanguageType_JScript</span><span class="sxs-lookup"><span data-stu-id="7c867-124">CorSym_LanguageType_JScript</span></span>|<span data-ttu-id="7c867-125">JScript 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-125">Indicates the JScript language.</span></span>|  
|<span data-ttu-id="7c867-126">CorSym_LanguageType_SMC</span><span class="sxs-lookup"><span data-stu-id="7c867-126">CorSym_LanguageType_SMC</span></span>|<span data-ttu-id="7c867-127">SMC 言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-127">Indicates the SMC language.</span></span>|  
|<span data-ttu-id="7c867-128">CorSym_LanguageType_MCPlusPlus</span><span class="sxs-lookup"><span data-stu-id="7c867-128">CorSym_LanguageType_MCPlusPlus</span></span>|<span data-ttu-id="7c867-129">C++ 言語の .NET Framework を有効になっていることを示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-129">Indicates the C++ language enabled for the .NET Framework.</span></span>|  
  
## <a name="language-vendor-constants"></a><span data-ttu-id="7c867-130">言語の仕入先定数</span><span class="sxs-lookup"><span data-stu-id="7c867-130">Language Vendor Constants</span></span>  
 <span data-ttu-id="7c867-131">次の表は、ベンダーの定数は、プログラミング言語のベンダーを識別する Guid を表す言語を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-131">The following table shows language vendor constants, which represent GUIDs that identify programming language vendors.</span></span>  
  
|<span data-ttu-id="7c867-132">シンボル</span><span class="sxs-lookup"><span data-stu-id="7c867-132">Symbol</span></span>|<span data-ttu-id="7c867-133">説明</span><span class="sxs-lookup"><span data-stu-id="7c867-133">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c867-134">CorSym_LanguageVendor_Microsoft</span><span class="sxs-lookup"><span data-stu-id="7c867-134">CorSym_LanguageVendor_Microsoft</span></span>|<span data-ttu-id="7c867-135">Microsoft を示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-135">Indicates Microsoft.</span></span>|  
  
## <a name="document-type-constants"></a><span data-ttu-id="7c867-136">ドキュメント型定数</span><span class="sxs-lookup"><span data-stu-id="7c867-136">Document Type Constants</span></span>  
 <span data-ttu-id="7c867-137">次の表は、ドキュメントの種類を識別する Guid を表す型定数は、ドキュメントを示します。</span><span class="sxs-lookup"><span data-stu-id="7c867-137">The following table shows document type constants, which represent GUIDs that identify document types.</span></span>  
  
|<span data-ttu-id="7c867-138">シンボル</span><span class="sxs-lookup"><span data-stu-id="7c867-138">Symbol</span></span>|<span data-ttu-id="7c867-139">説明</span><span class="sxs-lookup"><span data-stu-id="7c867-139">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="7c867-140">CorSym_DocumentType_Text</span><span class="sxs-lookup"><span data-stu-id="7c867-140">CorSym_DocumentType_Text</span></span>|<span data-ttu-id="7c867-141">テキスト ドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="7c867-141">Indicates a text document.</span></span>|  
|<span data-ttu-id="7c867-142">CorSym_DocumentType_MC</span><span class="sxs-lookup"><span data-stu-id="7c867-142">CorSym_DocumentType_MC</span></span>|<span data-ttu-id="7c867-143">テキスト以外のドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="7c867-143">Indicates a non-text document.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c867-144">関連項目</span><span class="sxs-lookup"><span data-stu-id="7c867-144">See Also</span></span>  
 [<span data-ttu-id="7c867-145">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="7c867-145">Unmanaged API Reference</span></span>](../../../docs/framework/unmanaged-api/index.md)
