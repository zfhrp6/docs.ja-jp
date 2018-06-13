---
title: IMetaDataTables::GetTableIndex メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetTableIndex
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetTableIndex
helpviewer_keywords:
- GetTableIndex method [.NET Framework metadata]
- IMetaDataTables::GetTableIndex method [.NET Framework metadata]
ms.assetid: c6ec3800-e0d9-4387-afb8-ddc0b818114c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d207eae5e9ac1b3020216226442321e72840c037
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33450363"
---
# <a name="imetadatatablesgettableindex-method"></a><span data-ttu-id="5a935-102">IMetaDataTables::GetTableIndex メソッド</span><span class="sxs-lookup"><span data-stu-id="5a935-102">IMetaDataTables::GetTableIndex Method</span></span>
<span data-ttu-id="5a935-103">指定したトークンによって参照されるテーブルのインデックスを取得します。</span><span class="sxs-lookup"><span data-stu-id="5a935-103">Gets the index for the table referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5a935-104">構文</span><span class="sxs-lookup"><span data-stu-id="5a935-104">Syntax</span></span>  
  
```  
HRESULT GetTableIndex (  
    [in]  ULONG   token,  
    [out] ULONG   *pixTbl  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5a935-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5a935-105">Parameters</span></span>  
 `token`  
 <span data-ttu-id="5a935-106">[in]テーブルを参照するトークンです。</span><span class="sxs-lookup"><span data-stu-id="5a935-106">[in] The token that references the table.</span></span>  
  
 `pixTbl`  
 <span data-ttu-id="5a935-107">[out]参照先のテーブルを取得するインデックスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5a935-107">[out] A pointer to the returned index for the referenced table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5a935-108">コメント</span><span class="sxs-lookup"><span data-stu-id="5a935-108">Remarks</span></span>  
 <span data-ttu-id="5a935-109">このメソッドの使用方法は、一貫性のある結果を返さないためお勧めしませんしないでください。</span><span class="sxs-lookup"><span data-stu-id="5a935-109">We do not recommend the use of this method, because it does not return consistent results.</span></span> <span data-ttu-id="5a935-110">GUID のテーブルについては、共通言語基盤 (CLI) ドキュメント、特に「Partition II:: Metadata Definition and Semantics」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a935-110">For information about the GUID table, see the Common Language Infrastructure (CLI) documentation, especially "Partition II: Metadata Definition and Semantics".</span></span> <span data-ttu-id="5a935-111">ドキュメントはオンラインで入手できます。MSDN の「[ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212)」 (ECMA の C# および共通言語基盤の標準規格) と、ECMA のインターナショナル Web サイトにある「[Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="5a935-111">The documentation is available online; see [ECMA C# and Common Language Infrastructure Standards](http://go.microsoft.com/fwlink/?LinkID=99212) on MSDN and [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://go.microsoft.com/fwlink/?LinkID=65552) on the Ecma International Web site.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5a935-112">要件</span><span class="sxs-lookup"><span data-stu-id="5a935-112">Requirements</span></span>  
 <span data-ttu-id="5a935-113">**プラットフォーム:** を参照してください[システム要件](../../../../docs/framework/get-started/system-requirements.md)です。</span><span class="sxs-lookup"><span data-stu-id="5a935-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5a935-114">**ヘッダー:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="5a935-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="5a935-115">**ライブラリ:** MsCorEE.dll にリソースとして使用</span><span class="sxs-lookup"><span data-stu-id="5a935-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="5a935-116">**.NET framework のバージョン:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5a935-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5a935-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="5a935-117">See Also</span></span>  
 [<span data-ttu-id="5a935-118">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a935-118">IMetaDataTables Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables-interface.md)  
 [<span data-ttu-id="5a935-119">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5a935-119">IMetaDataTables2 Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/imetadatatables2-interface.md)
