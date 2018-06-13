---
title: Contract1
ms.date: 03/30/2017
ms.assetid: aa00f6b3-7e1f-4213-841a-206463fca20b
ms.openlocfilehash: 12b45c08a3d8dc69e740ce77d0d2abd097907ac2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485708"
---
# <a name="contract"></a><span data-ttu-id="ba833-102">コントラクト</span><span class="sxs-lookup"><span data-stu-id="ba833-102">Contract</span></span>
<span data-ttu-id="ba833-103">コントラクト</span><span class="sxs-lookup"><span data-stu-id="ba833-103">Contract</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba833-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba833-104">Syntax</span></span>  
  
```  
class Contract  
{  
  sint32 AppDomainId;  
  Behavior Behaviors[];  
  string Name;  
  string Namespace;  
  Operation Operations[];  
  sint32 ProcessId;  
  Contract ref;  
  string SessionMode;  
  string Type;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ba833-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ba833-105">Methods</span></span>  
 <span data-ttu-id="ba833-106">Contract クラスで定義されているメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="ba833-106">The Contract class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ba833-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ba833-107">Properties</span></span>  
 <span data-ttu-id="ba833-108">Contract クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ba833-108">The Contract class has the following properties:</span></span>  
  
### <a name="appdomainid"></a><span data-ttu-id="ba833-109">AppDomainId</span><span class="sxs-lookup"><span data-stu-id="ba833-109">AppDomainId</span></span>  
 <span data-ttu-id="ba833-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ba833-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba833-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-112">コントラクトをホストする appdomain の appdomain ID。</span><span class="sxs-lookup"><span data-stu-id="ba833-112">The appdomain id of the appdomain that hosts the contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="ba833-113">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="ba833-113">Behaviors</span></span>  
 <span data-ttu-id="ba833-114">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="ba833-114">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="ba833-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-116">このコントラクトに関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="ba833-116">The behaviors associated with this contract.</span></span>  
  
### <a name="name"></a><span data-ttu-id="ba833-117">名前</span><span class="sxs-lookup"><span data-stu-id="ba833-117">Name</span></span>  
 <span data-ttu-id="ba833-118">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ba833-118">Data type: string</span></span>  
  
 <span data-ttu-id="ba833-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-120">WSDL でのコントラクトの名前。</span><span class="sxs-lookup"><span data-stu-id="ba833-120">The name of the contract in WSDL.</span></span>  
  
### <a name="namespace"></a><span data-ttu-id="ba833-121">名前空間</span><span class="sxs-lookup"><span data-stu-id="ba833-121">Namespace</span></span>  
 <span data-ttu-id="ba833-122">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ba833-122">Data type: string</span></span>  
  
 <span data-ttu-id="ba833-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-124">WSDL での `portType` 要素の名前空間。</span><span class="sxs-lookup"><span data-stu-id="ba833-124">The namespace of the `portType` element in WSDL.</span></span>  
  
### <a name="operations"></a><span data-ttu-id="ba833-125">操作</span><span class="sxs-lookup"><span data-stu-id="ba833-125">Operations</span></span>  
 <span data-ttu-id="ba833-126">データ型 : Operation 配列</span><span class="sxs-lookup"><span data-stu-id="ba833-126">Data type: Operation array</span></span>  
  
 <span data-ttu-id="ba833-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-128">このコントラクトの操作。</span><span class="sxs-lookup"><span data-stu-id="ba833-128">The operations of this contract.</span></span>  
  
### <a name="processid"></a><span data-ttu-id="ba833-129">ProcessId</span><span class="sxs-lookup"><span data-stu-id="ba833-129">ProcessId</span></span>  
 <span data-ttu-id="ba833-130">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ba833-130">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba833-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-132">コントラクトをホストするプロセスのプロセス ID。</span><span class="sxs-lookup"><span data-stu-id="ba833-132">The process Id of the process that hosts the contract.</span></span>  
  
### <a name="ref"></a><span data-ttu-id="ba833-133">ref</span><span class="sxs-lookup"><span data-stu-id="ba833-133">ref</span></span>  
 <span data-ttu-id="ba833-134">データ型 : Contract</span><span class="sxs-lookup"><span data-stu-id="ba833-134">Data type: Contract</span></span>  
  
 <span data-ttu-id="ba833-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-136">コントラクトが双方向コントラクトのときのコールバックの型。</span><span class="sxs-lookup"><span data-stu-id="ba833-136">The type of callback when the contract is a duplex contract.</span></span>  
  
### <a name="sessionmode"></a><span data-ttu-id="ba833-137">SessionMode</span><span class="sxs-lookup"><span data-stu-id="ba833-137">SessionMode</span></span>  
 <span data-ttu-id="ba833-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ba833-138">Data type: string</span></span>  
  
 <span data-ttu-id="ba833-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-140">コントラクトでチャネル セッションを使用するために、このコントラクトに関連付けられたバインディングが必要かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ba833-140">Indicates whether the contract requires the binding associated with this contract to use channel sessions.</span></span>  
  
### <a name="type"></a><span data-ttu-id="ba833-141">型</span><span class="sxs-lookup"><span data-stu-id="ba833-141">Type</span></span>  
 <span data-ttu-id="ba833-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="ba833-142">Data type: string</span></span>  
  
 <span data-ttu-id="ba833-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba833-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba833-144">コントラクトの型。</span><span class="sxs-lookup"><span data-stu-id="ba833-144">The type of the contract.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba833-145">要件</span><span class="sxs-lookup"><span data-stu-id="ba833-145">Requirements</span></span>  
  
|<span data-ttu-id="ba833-146">MOF</span><span class="sxs-lookup"><span data-stu-id="ba833-146">MOF</span></span>|<span data-ttu-id="ba833-147">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ba833-147">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ba833-148">Namespace</span><span class="sxs-lookup"><span data-stu-id="ba833-148">Namespace</span></span>|<span data-ttu-id="ba833-149">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ba833-149">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba833-150">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba833-150">See Also</span></span>  
 <xref:System.ServiceModel.Description.ContractDescription>
