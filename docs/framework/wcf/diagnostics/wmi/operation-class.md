---
title: "操作クラス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b19d1496-ef06-4d0c-b2ae-e728ec00cca0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54566bc452baa2e02cef7d8d13d29fcd5864c95c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="operation-class"></a><span data-ttu-id="926e4-102">操作クラス</span><span class="sxs-lookup"><span data-stu-id="926e4-102">Operation class</span></span>
<span data-ttu-id="926e4-103">操作</span><span class="sxs-lookup"><span data-stu-id="926e4-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="926e4-104">構文</span><span class="sxs-lookup"><span data-stu-id="926e4-104">Syntax</span></span>  
  
```  
class Operation  
{  
  string Action;  
  boolean AsyncPattern;  
  Behavior Behaviors[];  
  boolean IsCallback;  
  boolean IsInitiating;  
  boolean IsOneWay;  
  boolean IsTerminating;  
  string MethodSignature;  
  string Name;  
  string ParameterTypes[];  
  string ReplyAction;  
  string ReturnType;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="926e4-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="926e4-105">Methods</span></span>  
 <span data-ttu-id="926e4-106">Operation クラスで定義されているメソッドはありせん。</span><span class="sxs-lookup"><span data-stu-id="926e4-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="926e4-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="926e4-107">Properties</span></span>  
 <span data-ttu-id="926e4-108">Operation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="926e4-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="926e4-109">アクション</span><span class="sxs-lookup"><span data-stu-id="926e4-109">Action</span></span>  
 <span data-ttu-id="926e4-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="926e4-110">Data type: string</span></span>  
  
 <span data-ttu-id="926e4-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-112">要求メッセージの WS-Addressing 操作。</span><span class="sxs-lookup"><span data-stu-id="926e4-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="926e4-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="926e4-113">AsyncPattern</span></span>  
 <span data-ttu-id="926e4-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="926e4-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="926e4-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-116">非同期的を使用して、操作を実装することを示す、 `Begin`[開く/閉じる山かっこ] と`End`サービス コントラクトで [開く/閉じる山かっこ] メソッドのペア。</span><span class="sxs-lookup"><span data-stu-id="926e4-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="926e4-117">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="926e4-117">Behaviors</span></span>  
 <span data-ttu-id="926e4-118">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="926e4-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="926e4-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-120">この操作に関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="926e4-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="926e4-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="926e4-121">IsCallback</span></span>  
 <span data-ttu-id="926e4-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="926e4-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="926e4-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-124">この操作がコールバック操作の場合、True。</span><span class="sxs-lookup"><span data-stu-id="926e4-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="926e4-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="926e4-125">IsInitiating</span></span>  
 <span data-ttu-id="926e4-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="926e4-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="926e4-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-128">メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="926e4-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="926e4-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="926e4-129">IsOneWay</span></span>  
 <span data-ttu-id="926e4-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="926e4-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="926e4-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-132">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="926e4-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="926e4-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="926e4-133">IsTerminating</span></span>  
 <span data-ttu-id="926e4-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="926e4-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="926e4-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-136">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="926e4-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="926e4-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="926e4-137">MethodSignature</span></span>  
 <span data-ttu-id="926e4-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="926e4-138">Data type: string</span></span>  
  
 <span data-ttu-id="926e4-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-140">操作のメソッド署名。</span><span class="sxs-lookup"><span data-stu-id="926e4-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="926e4-141">name</span><span class="sxs-lookup"><span data-stu-id="926e4-141">Name</span></span>  
 <span data-ttu-id="926e4-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="926e4-142">Data type: string</span></span>  
  
 <span data-ttu-id="926e4-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-144">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="926e4-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="926e4-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="926e4-145">ParameterTypes</span></span>  
 <span data-ttu-id="926e4-146">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="926e4-146">Data type: string array</span></span>  
  
 <span data-ttu-id="926e4-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-148">操作のパラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="926e4-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="926e4-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="926e4-149">ReplyAction</span></span>  
 <span data-ttu-id="926e4-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="926e4-150">Data type: string</span></span>  
  
 <span data-ttu-id="926e4-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-152">操作の応答メッセージの SOAP アクションの値。</span><span class="sxs-lookup"><span data-stu-id="926e4-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="926e4-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="926e4-153">ReturnType</span></span>  
 <span data-ttu-id="926e4-154">データ型: string</span><span class="sxs-lookup"><span data-stu-id="926e4-154">Data type: string</span></span>  
  
 <span data-ttu-id="926e4-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="926e4-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="926e4-156">操作の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="926e4-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="926e4-157">必要条件</span><span class="sxs-lookup"><span data-stu-id="926e4-157">Requirements</span></span>  
  
|<span data-ttu-id="926e4-158">MOF</span><span class="sxs-lookup"><span data-stu-id="926e4-158">MOF</span></span>|<span data-ttu-id="926e4-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="926e4-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="926e4-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="926e4-160">Namespace</span></span>|<span data-ttu-id="926e4-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="926e4-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="926e4-162">参照</span><span class="sxs-lookup"><span data-stu-id="926e4-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
