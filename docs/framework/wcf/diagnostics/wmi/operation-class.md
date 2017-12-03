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
ms.openlocfilehash: 492a3cb4b11706bfabc42976fb1adfad24a2279a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="operation-class"></a><span data-ttu-id="8bbbe-102">操作クラス</span><span class="sxs-lookup"><span data-stu-id="8bbbe-102">Operation class</span></span>
<span data-ttu-id="8bbbe-103">操作</span><span class="sxs-lookup"><span data-stu-id="8bbbe-103">Operation</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bbbe-104">構文</span><span class="sxs-lookup"><span data-stu-id="8bbbe-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8bbbe-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8bbbe-105">Methods</span></span>  
 <span data-ttu-id="8bbbe-106">Operation クラスで定義されているメソッドはありせん。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-106">The Operation class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8bbbe-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="8bbbe-107">Properties</span></span>  
 <span data-ttu-id="8bbbe-108">Operation クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-108">The Operation class has the following properties:</span></span>  
  
### <a name="action"></a><span data-ttu-id="8bbbe-109">アクション</span><span class="sxs-lookup"><span data-stu-id="8bbbe-109">Action</span></span>  
 <span data-ttu-id="8bbbe-110">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8bbbe-110">Data type: string</span></span>  
  
 <span data-ttu-id="8bbbe-111">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-112">要求メッセージの WS-Addressing 操作。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-112">The WS-Addressing action of the request message.</span></span>  
  
### <a name="asyncpattern"></a><span data-ttu-id="8bbbe-113">AsyncPattern</span><span class="sxs-lookup"><span data-stu-id="8bbbe-113">AsyncPattern</span></span>  
 <span data-ttu-id="8bbbe-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8bbbe-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bbbe-115">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-116">非同期的を使用して、操作を実装することを示す、 `Begin`[開く/閉じる山かっこ] と`End`サービス コントラクトで [開く/閉じる山かっこ] メソッドのペア。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-116">Indicates that an operation is implemented asynchronously using a `Begin`[open/close angle brackets] and `End`[open/close angle brackets] method pair in a service contract.</span></span>  
  
### <a name="behaviors"></a><span data-ttu-id="8bbbe-117">ビヘイビアー</span><span class="sxs-lookup"><span data-stu-id="8bbbe-117">Behaviors</span></span>  
 <span data-ttu-id="8bbbe-118">データ型 : Behavior array</span><span class="sxs-lookup"><span data-stu-id="8bbbe-118">Data type: Behavior array</span></span>  
  
 <span data-ttu-id="8bbbe-119">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-120">この操作に関連付けられている動作。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-120">The behaviors associated with this operation.</span></span>  
  
### <a name="iscallback"></a><span data-ttu-id="8bbbe-121">IsCallback</span><span class="sxs-lookup"><span data-stu-id="8bbbe-121">IsCallback</span></span>  
 <span data-ttu-id="8bbbe-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8bbbe-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bbbe-123">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-124">この操作がコールバック操作の場合、True。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-124">True when the operation is a callback operation.</span></span>  
  
### <a name="isinitiating"></a><span data-ttu-id="8bbbe-125">IsInitiating</span><span class="sxs-lookup"><span data-stu-id="8bbbe-125">IsInitiating</span></span>  
 <span data-ttu-id="8bbbe-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8bbbe-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bbbe-127">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-128">メソッドが、サーバーでセッションを開始できる操作を実装するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-128">Indicates whether the method implements an operation that can initiate a session on the server.</span></span>  
  
### <a name="isoneway"></a><span data-ttu-id="8bbbe-129">IsOneWay</span><span class="sxs-lookup"><span data-stu-id="8bbbe-129">IsOneWay</span></span>  
 <span data-ttu-id="8bbbe-130">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8bbbe-130">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bbbe-131">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-131">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-132">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-132">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="isterminating"></a><span data-ttu-id="8bbbe-133">IsTerminating</span><span class="sxs-lookup"><span data-stu-id="8bbbe-133">IsTerminating</span></span>  
 <span data-ttu-id="8bbbe-134">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="8bbbe-134">Data type: boolean</span></span>  
  
 <span data-ttu-id="8bbbe-135">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-135">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-136">操作が応答メッセージを返すかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-136">Indicates whether an operation returns a reply message.</span></span>  
  
### <a name="methodsignature"></a><span data-ttu-id="8bbbe-137">MethodSignature</span><span class="sxs-lookup"><span data-stu-id="8bbbe-137">MethodSignature</span></span>  
 <span data-ttu-id="8bbbe-138">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8bbbe-138">Data type: string</span></span>  
  
 <span data-ttu-id="8bbbe-139">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-139">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-140">操作のメソッド署名。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-140">The method signature of the operation.</span></span>  
  
### <a name="name"></a><span data-ttu-id="8bbbe-141">名前</span><span class="sxs-lookup"><span data-stu-id="8bbbe-141">Name</span></span>  
 <span data-ttu-id="8bbbe-142">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8bbbe-142">Data type: string</span></span>  
  
 <span data-ttu-id="8bbbe-143">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-143">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-144">操作の名前。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-144">The name of the operation.</span></span>  
  
### <a name="parametertypes"></a><span data-ttu-id="8bbbe-145">ParameterTypes</span><span class="sxs-lookup"><span data-stu-id="8bbbe-145">ParameterTypes</span></span>  
 <span data-ttu-id="8bbbe-146">データ型 : string array</span><span class="sxs-lookup"><span data-stu-id="8bbbe-146">Data type: string array</span></span>  
  
 <span data-ttu-id="8bbbe-147">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-147">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-148">操作のパラメーターの型。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-148">The types of the parameters of the operation.</span></span>  
  
### <a name="replyaction"></a><span data-ttu-id="8bbbe-149">ReplyAction</span><span class="sxs-lookup"><span data-stu-id="8bbbe-149">ReplyAction</span></span>  
 <span data-ttu-id="8bbbe-150">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8bbbe-150">Data type: string</span></span>  
  
 <span data-ttu-id="8bbbe-151">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-151">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-152">操作の応答メッセージの SOAP アクションの値。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-152">The value of the SOAP action for the reply message of the operation.</span></span>  
  
### <a name="returntype"></a><span data-ttu-id="8bbbe-153">ReturnType</span><span class="sxs-lookup"><span data-stu-id="8bbbe-153">ReturnType</span></span>  
 <span data-ttu-id="8bbbe-154">データ型: string</span><span class="sxs-lookup"><span data-stu-id="8bbbe-154">Data type: string</span></span>  
  
 <span data-ttu-id="8bbbe-155">アクセスの種類 : 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="8bbbe-155">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8bbbe-156">操作の戻り値の型。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-156">The return type of the operation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bbbe-157">要件</span><span class="sxs-lookup"><span data-stu-id="8bbbe-157">Requirements</span></span>  
  
|<span data-ttu-id="8bbbe-158">MOF</span><span class="sxs-lookup"><span data-stu-id="8bbbe-158">MOF</span></span>|<span data-ttu-id="8bbbe-159">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="8bbbe-159">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8bbbe-160">Namespace</span><span class="sxs-lookup"><span data-stu-id="8bbbe-160">Namespace</span></span>|<span data-ttu-id="8bbbe-161">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="8bbbe-161">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8bbbe-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="8bbbe-162">See Also</span></span>  
 <xref:System.ServiceModel.Description.OperationDescription>
