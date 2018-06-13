---
title: シンボル ストア診断インターフェイス
ms.date: 03/30/2017
helpviewer_keywords:
- unmanaged interfaces [.NET Framework], debugging
- diagnostics symbol store interfaces [.NET Framework]
- interfaces [.NET Framework], diagnostics symbol store
- unmanaged interfaces [.NET Framework], diagnostics symbol store
- debugging interfaces [.NET Framework]
- interfaces [.NET Framework debugging]
ms.assetid: f96987d5-e6a5-478b-ac5e-302e16545cce
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6fca7359888b8b73b2e1cf709ab708d71abf0db6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33435813"
---
# <a name="diagnostics-symbol-store-interfaces"></a><span data-ttu-id="3a612-102">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-102">Diagnostics Symbol Store Interfaces</span></span>
<span data-ttu-id="3a612-103">このトピックでは、デバッガーで使用するためのシンボル情報を生成するコンパイラを有効にするアンマネージ インターフェイスについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3a612-103">This topic describes the unmanaged interfaces that enable a compiler to generate symbol information for use by a debugger.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a612-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3a612-104">In This Section</span></span>  
 [<span data-ttu-id="3a612-105">IBindingDisplay インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-105">IBindingDisplay Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/ibindingdisplay-interface.md)  
 <span data-ttu-id="3a612-106">実行中のアプリケーションに関する現在のバインド情報を表示するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-106">Provides methods that display current binding information about the running application.</span></span>  
  
 [<span data-ttu-id="3a612-107">IDebugAutoAttach インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-107">IDebugAutoAttach Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/idebugautoattach-interface.md)  
 <span data-ttu-id="3a612-108">サーバー起動デバッガーの自動アタッチ用インターフェイスを定義します。</span><span class="sxs-lookup"><span data-stu-id="3a612-108">Defines the interface for a server-invoked debugger auto attach.</span></span>  
  
 [<span data-ttu-id="3a612-109">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-109">INotifyConnection2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifyconnection2-interface.md)  
 <span data-ttu-id="3a612-110">登録および接続通知ソースの登録を解除するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a612-110">Declares methods for registering and unregistering a connection notification source.</span></span>  
  
 [<span data-ttu-id="3a612-111">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-111">INotifySink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysink2-interface.md)  
 <span data-ttu-id="3a612-112">シンクの通知のためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a612-112">Declares methods for sink notification.</span></span>  
  
 [<span data-ttu-id="3a612-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-113">INotifySource2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/inotifysource2-interface.md)  
 <span data-ttu-id="3a612-114">通知フィルターを設定するためのメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="3a612-114">Declares a method for setting notification filters.</span></span>  
  
 [<span data-ttu-id="3a612-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-115">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)  
 <span data-ttu-id="3a612-116">エディット コンティニュ機能についてを説明します。</span><span class="sxs-lookup"><span data-stu-id="3a612-116">Provides information for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="3a612-117">ISymUnmanagedAsyncMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-117">ISymUnmanagedAsyncMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethod-interface.md)  
 <span data-ttu-id="3a612-118">このインターフェイスは、読み取りの補足[ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)です。</span><span class="sxs-lookup"><span data-stu-id="3a612-118">This interface is the reading complement to [ISymUnmanagedAsyncMethodPropertiesWriter Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md).</span></span>  
  
 [<span data-ttu-id="3a612-119">ISymUnmanagedAsyncMethodPropertiesWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-119">ISymUnmanagedAsyncMethodPropertiesWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedasyncmethodpropertieswriter-interface.md)  
 <span data-ttu-id="3a612-120">メソッドのシンボルごとに省略可能な非同期メソッド情報を定義をできます。</span><span class="sxs-lookup"><span data-stu-id="3a612-120">Allows definition of optional async method information per method symbol.</span></span> <span data-ttu-id="3a612-121">開かれたメソッドで使用する必要があります (つまり、呼び出しの間、 [OpenMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)と[CloseMethod メソッド](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md))。</span><span class="sxs-lookup"><span data-stu-id="3a612-121">Must use with an opened method (that is, between calls to the [OpenMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-openmethod-method.md)and the [CloseMethod Method](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-closemethod-method.md)).</span></span>  
  
 [<span data-ttu-id="3a612-122">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-122">ISymUnmanagedBinder Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder-interface.md)  
 <span data-ttu-id="3a612-123">アンマネージ コードのシンボル バインダーを表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-123">Represents a symbol binder for unmanaged code.</span></span>  
  
 [<span data-ttu-id="3a612-124">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-124">ISymUnmanagedBinder2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder2-interface.md)  
 <span data-ttu-id="3a612-125">アンマネージ コードのシンボル バインダーを表し、拡張、`ISymUnmanagedBinder`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-125">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="3a612-126">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-126">ISymUnmanagedBinder3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedbinder3-interface.md)  
 <span data-ttu-id="3a612-127">アンマネージ コードのシンボル バインダーを表し、拡張、`ISymUnmanagedBinder`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-127">Represents a symbol binder for unmanaged code, and extends the `ISymUnmanagedBinder` interface.</span></span>  
  
 [<span data-ttu-id="3a612-128">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-128">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 <span data-ttu-id="3a612-129">アンマネージ定数へのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-129">Provides access to unmanaged constants.</span></span>  
  
 [<span data-ttu-id="3a612-130">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-130">ISymUnmanagedDispose Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddispose-interface.md)  
 <span data-ttu-id="3a612-131">アンマネージ リソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="3a612-131">Disposes of unmanaged resources.</span></span>  
  
 [<span data-ttu-id="3a612-132">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-132">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)  
 <span data-ttu-id="3a612-133">シンボル ストアによって参照されるドキュメントを表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-133">Represents a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="3a612-134">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-134">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)  
 <span data-ttu-id="3a612-135">シンボル ストアで参照されるドキュメントに書き込むためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-135">Provides methods for writing to a document referenced by a symbol store.</span></span>  
  
 [<span data-ttu-id="3a612-136">ISymUnmanagedENCUpdate インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-136">ISymUnmanagedENCUpdate Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedencupdate-interface.md)  
 <span data-ttu-id="3a612-137">エディット コンティニュ機能のメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-137">Provides methods for the Edit and Continue feature.</span></span>  
  
 [<span data-ttu-id="3a612-138">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-138">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)  
 <span data-ttu-id="3a612-139">シンボル ストア内のメソッドを表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-139">Represents a method within the symbol store.</span></span>  
  
 [<span data-ttu-id="3a612-140">ISymUnmanagedNamespace インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-140">ISymUnmanagedNamespace Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md)  
 <span data-ttu-id="3a612-141">名前空間を表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-141">Represents a namespace.</span></span>  
  
 [<span data-ttu-id="3a612-142">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-142">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)  
 <span data-ttu-id="3a612-143">ドキュメント、メソッド、およびシンボル ストア内の変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-143">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span>  
  
 [<span data-ttu-id="3a612-144">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-144">ISymUnmanagedReader2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader2-interface.md)  
 <span data-ttu-id="3a612-145">メソッドのトークンと編集、コピーのバージョン番号を指定して、シンボル リーダー メソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="3a612-145">Gets a symbol reader method given a method token and an edit-and-copy version number.</span></span>  
  
 [<span data-ttu-id="3a612-146">ISymUnmanagedReaderSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-146">ISymUnmanagedReaderSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreadersymbolsearchinfo-interface.md)  
 <span data-ttu-id="3a612-147">シンボル検索情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-147">Provides methods that get symbol search information.</span></span>  
  
 [<span data-ttu-id="3a612-148">ISymUnmanagedScope インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-148">ISymUnmanagedScope Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md)  
 <span data-ttu-id="3a612-149">メソッド内での構文のスコープを表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-149">Represents a lexical scope within a method.</span></span>  
  
 [<span data-ttu-id="3a612-150">ISymUnmanagedScope2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-150">ISymUnmanagedScope2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope2-interface.md)  
 <span data-ttu-id="3a612-151">メソッド内の構文のスコープを表し、拡張、`ISymUnmanagedScope`スコープ内で定義されている定数に関する情報を取得するメソッドを持つインターフェイス.</span><span class="sxs-lookup"><span data-stu-id="3a612-151">Represents a lexical scope within a method, and extends the `ISymUnmanagedScope` interface with methods that get information about constants defined within the scope..</span></span>  
  
 [<span data-ttu-id="3a612-152">ISymUnmanagedSourceServerModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-152">ISymUnmanagedSourceServerModule Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsourceservermodule-interface.md)  
 <span data-ttu-id="3a612-153">モジュールのソース サーバーのデータを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-153">Provides source server data for a module.</span></span>  
  
 [<span data-ttu-id="3a612-154">ISymUnmanagedSymbolSearchInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-154">ISymUnmanagedSymbolSearchInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedsymbolsearchinfo-interface.md)  
 <span data-ttu-id="3a612-155">検索パスに関する情報を取得するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-155">Provides methods that get information about the search path.</span></span>  
  
 [<span data-ttu-id="3a612-156">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-156">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 <span data-ttu-id="3a612-157">パラメーター、ローカル変数またはフィールドなどの変数を表します。</span><span class="sxs-lookup"><span data-stu-id="3a612-157">Represents a variable, such as a parameter, a local variable, or a field.</span></span>  
  
 [<span data-ttu-id="3a612-158">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-158">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)  
 <span data-ttu-id="3a612-159">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-159">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
 [<span data-ttu-id="3a612-160">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-160">ISymUnmanagedWriter2 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter2-interface.md)  
 <span data-ttu-id="3a612-161">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-161">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="3a612-162">拡張、`ISymUnmanagedWriter`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-162">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="3a612-163">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-163">ISymUnmanagedWriter3 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter3-interface.md)  
 <span data-ttu-id="3a612-164">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文のスコープ、および変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="3a612-164">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="3a612-165">拡張、`ISymUnmanagedWriter`インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-165">Extends the `ISymUnmanagedWriter` interface.</span></span>  
  
 [<span data-ttu-id="3a612-166">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-166">ISymUnmanagedWriter4 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter4-interface.md)  
 <span data-ttu-id="3a612-167">ISymUnmanagedWriter4 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-167">ISymUnmanagedWriter4 interface.</span></span>  
  
 [<span data-ttu-id="3a612-168">ISymUnmanagedWriter5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3a612-168">ISymUnmanagedWriter5 Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter5-interface.md)  
 <span data-ttu-id="3a612-169">ISymUnmanagedWriter5 インターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="3a612-169">ISymUnmanagedWriter5 interface.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a612-170">関連項目</span><span class="sxs-lookup"><span data-stu-id="3a612-170">Related Sections</span></span>  
 [<span data-ttu-id="3a612-171">シンボル ストア診断列挙型</span><span class="sxs-lookup"><span data-stu-id="3a612-171">Diagnostics Symbol Store Enumerations</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)  
  
 [<span data-ttu-id="3a612-172">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="3a612-172">Diagnostics Symbol Store Structures</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-structures.md)  
  
 [<span data-ttu-id="3a612-173">デバッグ</span><span class="sxs-lookup"><span data-stu-id="3a612-173">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
