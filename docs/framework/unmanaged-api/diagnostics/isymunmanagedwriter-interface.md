---
title: "ISymUnmanagedWriter インターフェイス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f4996f0196df4c2bcf890df6ad972f313403e435
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriter-interface"></a><span data-ttu-id="47696-102">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47696-102">ISymUnmanagedWriter Interface</span></span>
<span data-ttu-id="47696-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="47696-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="47696-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-104">Methods</span></span>  
  
|<span data-ttu-id="47696-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-105">Method</span></span>|<span data-ttu-id="47696-106">説明</span><span class="sxs-lookup"><span data-stu-id="47696-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="47696-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-107">Abort Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-abort-method.md)|<span data-ttu-id="47696-108">シンボルをシンボル ストアにコミットせずシンボル ライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="47696-108">Closes the symbol writer without committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="47696-109">Close メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-109">Close Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-close-method.md)|<span data-ttu-id="47696-110">シンボルをシンボル ストアにコミットした後にシンボル ライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="47696-110">Closes the symbol writer after committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="47696-111">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-111">CloseMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)|<span data-ttu-id="47696-112">現在のメソッドを閉じます。</span><span class="sxs-lookup"><span data-stu-id="47696-112">Closes the current method.</span></span> <span data-ttu-id="47696-113">メソッドが閉じられた後は、内部にシンボルを定義できます。</span><span class="sxs-lookup"><span data-stu-id="47696-113">Once a method is closed, no more symbols can be defined within it.</span></span>|  
|[<span data-ttu-id="47696-114">CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-114">CloseNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closenamespace-method.md)|<span data-ttu-id="47696-115">終了では、名前空間、最も最近開いたします。</span><span class="sxs-lookup"><span data-stu-id="47696-115">Closes the most recently opened namespace.</span></span>|  
|[<span data-ttu-id="47696-116">CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-116">CloseScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closescope-method.md)|<span data-ttu-id="47696-117">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="47696-117">Closes the current lexical scope.</span></span>|  
|[<span data-ttu-id="47696-118">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-118">DefineConstant Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineconstant-method.md)|<span data-ttu-id="47696-119">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-119">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="47696-120">DefineDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-120">DefineDocument Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definedocument-method.md)|<span data-ttu-id="47696-121">ソース ドキュメントを定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-121">Defines a source document.</span></span>|  
|[<span data-ttu-id="47696-122">DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-122">DefineField Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definefield-method.md)|<span data-ttu-id="47696-123">メソッド内ではない 1 つの変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-123">Defines a single variable that is not within a method.</span></span>|  
|[<span data-ttu-id="47696-124">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-124">DefineGlobalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineglobalvariable-method.md)|<span data-ttu-id="47696-125">単一のグローバル変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-125">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="47696-126">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-126">DefineLocalVariable Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definelocalvariable-method.md)|<span data-ttu-id="47696-127">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-127">Defines a single variable in the current lexical scope.</span></span>|  
|[<span data-ttu-id="47696-128">DefineParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-128">DefineParameter Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-defineparameter-method.md)|<span data-ttu-id="47696-129">現在のメソッドの 1 つのパラメーターを定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-129">Defines a single parameter in the current method.</span></span>|  
|[<span data-ttu-id="47696-130">DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-130">DefineSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-definesequencepoints-method.md)|<span data-ttu-id="47696-131">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-131">Defines a group of sequence points within the current method.</span></span>|  
|[<span data-ttu-id="47696-132">GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-132">GetDebugInfo Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-getdebuginfo-method.md)|<span data-ttu-id="47696-133">ポータブル実行可能 (PE) ファイル ヘッダーのデバッグ ディレクトリ エントリを書き込むときにコンパイラに必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="47696-133">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span>|  
|[<span data-ttu-id="47696-134">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-134">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize-method.md)|<span data-ttu-id="47696-135">このライターが関連付けられるメタデータ エミッタ インターフェイスを設定し、デバッグ シンボルが書き込まれる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="47696-135">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>|  
|[<span data-ttu-id="47696-136">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-136">Initialize2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-initialize2-method.md)|<span data-ttu-id="47696-137">出力ファイル名のデバッグ シンボルが記述され、プログラム データベース (PDB) ファイルの最終的な場所に設定を設定、このライターが関連付けられるメタデータ エミッタ インターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="47696-137">Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.</span></span>|  
|[<span data-ttu-id="47696-138">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-138">OpenMethod Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)|<span data-ttu-id="47696-139">シンボル情報は生成先のメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="47696-139">Opens a method into which symbol information is emitted.</span></span>|  
|[<span data-ttu-id="47696-140">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-140">OpenNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-opennamespace-method.md)|<span data-ttu-id="47696-141">新しい名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="47696-141">Opens a new namespace.</span></span>|  
|[<span data-ttu-id="47696-142">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-142">OpenScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openscope-method.md)|<span data-ttu-id="47696-143">現在のメソッドの構文の新しいスコープを開きます。</span><span class="sxs-lookup"><span data-stu-id="47696-143">Opens a new lexical scope in the current method.</span></span>|  
|[<span data-ttu-id="47696-144">RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-144">RemapToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-remaptoken-method.md)|<span data-ttu-id="47696-145">メタデータの生成と、メタデータ トークンが再マップされたシンボル ライターを通知します。</span><span class="sxs-lookup"><span data-stu-id="47696-145">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span>|  
|[<span data-ttu-id="47696-146">SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-146">SetMethodSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setmethodsourcerange-method.md)|<span data-ttu-id="47696-147">実際の先頭とソース ファイル内のメソッドの末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="47696-147">Specifies the true start and end of a method within a source file.</span></span>|  
|[<span data-ttu-id="47696-148">SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-148">SetScopeRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setscoperange-method.md)|<span data-ttu-id="47696-149">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-149">Defines the offset range for the specified lexical scope.</span></span>|  
|[<span data-ttu-id="47696-150">SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-150">SetSymAttribute Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setsymattribute-method.md)|<span data-ttu-id="47696-151">その名前に基づくカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="47696-151">Defines a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="47696-152">SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-152">SetUserEntryPoint Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-setuserentrypoint-method.md)|<span data-ttu-id="47696-153">このモジュールのエントリ ポイントは、ユーザー定義のメソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="47696-153">Specifies the user-defined method that is the entry point for this module.</span></span>|  
|[<span data-ttu-id="47696-154">UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="47696-154">UsingNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-usingnamespace-method.md)|<span data-ttu-id="47696-155">現在開かれている構文スコープ内で指定した名前空間の完全修飾名を使用していることを指定します。</span><span class="sxs-lookup"><span data-stu-id="47696-155">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="47696-156">必要条件</span><span class="sxs-lookup"><span data-stu-id="47696-156">Requirements</span></span>  
 <span data-ttu-id="47696-157">**ヘッダー:** CorSym.idl、CorSym.h</span><span class="sxs-lookup"><span data-stu-id="47696-157">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47696-158">参照</span><span class="sxs-lookup"><span data-stu-id="47696-158">See Also</span></span>  
 [<span data-ttu-id="47696-159">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47696-159">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)  
 [<span data-ttu-id="47696-160">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47696-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 [<span data-ttu-id="47696-161">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="47696-161">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)
