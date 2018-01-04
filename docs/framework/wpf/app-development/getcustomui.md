---
title: GetCustomUI
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: custom error messages [WPF]
ms.assetid: e55180fc-35bb-4f80-a136-772b5eb3e4e5
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 88c2873a5929e25335b0c6ef64f8121e31177ab4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="getcustomui"></a><span data-ttu-id="b4517-102">GetCustomUI</span><span class="sxs-lookup"><span data-stu-id="b4517-102">GetCustomUI</span></span>
<span data-ttu-id="b4517-103">実装されている場合に、ホストからカスタムの進行状況とエラー メッセージを取得する PresentationHost.exe によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4517-103">Called by PresentationHost.exe to get custom progress and error messages from the host, if implemented.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4517-104">構文</span><span class="sxs-lookup"><span data-stu-id="b4517-104">Syntax</span></span>  
  
```  
HRESULT GetCustomUI( [out] BSTR* pwzProgressAssemblyName, [out] BSTR* pwzProgressClassName, [out] BSTR* pwzErrorAssemblyName, [out] BSTR* pwzErrorClassName );  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b4517-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b4517-105">Parameters</span></span>  
 `pwzProgressAssemblyName`  
  
 <span data-ttu-id="b4517-106">[out]進行中のホストが指定したユーザー インターフェイスが含まれるアセンブリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4517-106">[out] A pointer to the assembly that contains the host-supplied progress user interface.</span></span>  
  
 `pwzProgressClassName`  
  
 <span data-ttu-id="b4517-107">[out]可能であれば、実行中のホストが指定したユーザー インターフェイスであるクラスの名前、[!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)]ファイルと<xref:System.Windows.Controls.Page>は、最上位要素です。</span><span class="sxs-lookup"><span data-stu-id="b4517-107">[out] The name of the class that is the host-supplied progress user interface, preferably a [!INCLUDE[TLA#tla_titlexaml](../../../../includes/tlasharptla-titlexaml-md.md)] file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="b4517-108">このクラスがで指定されているアセンブリに存在`pwzProgressAssemblyName`です。</span><span class="sxs-lookup"><span data-stu-id="b4517-108">This class resides in the assembly that is specified by `pwzProgressAssemblyName`.</span></span>  
  
 `pwzErrorAssemblyName`  
  
 <span data-ttu-id="b4517-109">[out]ホストが指定したエラーのユーザー インターフェイスが含まれるアセンブリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="b4517-109">[out] A pointer to the assembly that contains the host-supplied error user interface.</span></span>  
  
 `pwzErrorClassName`  
  
 <span data-ttu-id="b4517-110">[out]ホストが指定したエラーのユーザーであるクラスの名前のインターフェイス、可能であればの XAML ファイル<xref:System.Windows.Controls.Page>は、最上位要素です。</span><span class="sxs-lookup"><span data-stu-id="b4517-110">[out] The name of the class that is the host-supplied error user interface, preferably a XAML file with <xref:System.Windows.Controls.Page> is its top-level element.</span></span> <span data-ttu-id="b4517-111">このクラスがで指定されているアセンブリに存在`pwzErrorAssemblyName`です。</span><span class="sxs-lookup"><span data-stu-id="b4517-111">This class resides in the assembly that is specified by `pwzErrorAssemblyName`.</span></span>  
  
## <a name="property-valuereturn-value"></a><span data-ttu-id="b4517-112">プロパティ値/戻り値</span><span class="sxs-lookup"><span data-stu-id="b4517-112">Property Value/Return Value</span></span>  
 <span data-ttu-id="b4517-113">HRESULT: 無視されます。</span><span class="sxs-lookup"><span data-stu-id="b4517-113">HRESULT: Ignored.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4517-114">コメント</span><span class="sxs-lookup"><span data-stu-id="b4517-114">Remarks</span></span>  
 <span data-ttu-id="b4517-115">ホスト アプリケーションに PresentationHost.exe の既定のユーザー インターフェイスが準拠していない特定のテーマがあります。</span><span class="sxs-lookup"><span data-stu-id="b4517-115">A host application may have a specific theme that PresentationHost.exe’s default user interfaces may not conform to.</span></span> <span data-ttu-id="b4517-116">大文字と小文字の場合は、ホスト アプリケーションを実装できます[ある GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) PresentationHost.exe に、ユーザー インターフェイスで進行状況とエラーが返される。</span><span class="sxs-lookup"><span data-stu-id="b4517-116">If this is the case, the host application can implement [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) to return progress and error user interfaces to PresentationHost.exe.</span></span> <span data-ttu-id="b4517-117">PresentationHost.exe が常に呼び出す[ある GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md)の既定のユーザー インターフェイスを使用する前にします。</span><span class="sxs-lookup"><span data-stu-id="b4517-117">PresentationHost.exe will always call [GetCustomUI](../../../../docs/framework/wpf/app-development/getcustomui.md) before using its default user interfaces.</span></span>  
  
 <span data-ttu-id="b4517-118">この関数は PresentationHost の初期化中に 1 回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4517-118">This function is called once during PresentationHost’s initialization.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4517-119">参照</span><span class="sxs-lookup"><span data-stu-id="b4517-119">See Also</span></span>  
 [<span data-ttu-id="b4517-120">IWpfHostSupport</span><span class="sxs-lookup"><span data-stu-id="b4517-120">IWpfHostSupport</span></span>](../../../../docs/framework/wpf/app-development/iwpfhostsupport.md)
