---
title: "OLE DB スキーマ コレクション"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e120ea532b6da455e31ce7345b6c4b2be1ec975f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="3a4cd-102">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="3a4cd-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="3a4cd-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3a4cd-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="3a4cd-104">Microsoft SQL Server OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="3a4cd-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="3a4cd-105">Microsoft SQL Server OLE DB Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="3a4cd-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3a4cd-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-106">Tables</span></span>  
  
-   <span data-ttu-id="3a4cd-107">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-107">Columns</span></span>  
  
-   <span data-ttu-id="3a4cd-108">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-108">Procedures</span></span>  
  
-   <span data-ttu-id="3a4cd-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3a4cd-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="3a4cd-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="3a4cd-110">Catalog</span></span>  
  
-   <span data-ttu-id="3a4cd-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3a4cd-112">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-112">Tables</span></span>  
  
|<span data-ttu-id="3a4cd-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-113">ColumnName</span></span>|<span data-ttu-id="3a4cd-114">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-115">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-116">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-116">String</span></span>|  
|<span data-ttu-id="3a4cd-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-118">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-118">String</span></span>|  
|<span data-ttu-id="3a4cd-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-119">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-120">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-120">String</span></span>|  
|<span data-ttu-id="3a4cd-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-121">TABLE_TYPE</span></span>|<span data-ttu-id="3a4cd-122">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-122">String</span></span>|  
|<span data-ttu-id="3a4cd-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-123">TABLE_GUID</span></span>|<span data-ttu-id="3a4cd-124">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-124">Guid</span></span>|  
|<span data-ttu-id="3a4cd-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-125">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-126">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-126">String</span></span>|  
|<span data-ttu-id="3a4cd-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-127">TABLE_PROPID</span></span>|<span data-ttu-id="3a4cd-128">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-128">Int64</span></span>|  
|<span data-ttu-id="3a4cd-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-129">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-130">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-131">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3a4cd-133">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-133">Columns</span></span>  
  
|<span data-ttu-id="3a4cd-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-134">ColumnName</span></span>|<span data-ttu-id="3a4cd-135">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-136">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-137">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-137">String</span></span>|  
|<span data-ttu-id="3a4cd-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-139">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-139">String</span></span>|  
|<span data-ttu-id="3a4cd-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-140">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-141">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-141">String</span></span>|  
|<span data-ttu-id="3a4cd-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-142">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-143">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-143">String</span></span>|  
|<span data-ttu-id="3a4cd-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-144">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-145">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-145">Guid</span></span>|  
|<span data-ttu-id="3a4cd-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-146">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-147">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-147">Int64</span></span>|  
|<span data-ttu-id="3a4cd-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-149">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-149">Int64</span></span>|  
|<span data-ttu-id="3a4cd-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3a4cd-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-151">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3a4cd-153">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-153">String</span></span>|  
|<span data-ttu-id="3a4cd-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="3a4cd-155">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-155">Int64</span></span>|  
|<span data-ttu-id="3a4cd-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-156">IS_NULLABLE</span></span>|<span data-ttu-id="3a4cd-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-157">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-158">DATA_TYPE</span></span>|<span data-ttu-id="3a4cd-159">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-159">Int32</span></span>|  
|<span data-ttu-id="3a4cd-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-160">TYPE_GUID</span></span>|<span data-ttu-id="3a4cd-161">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-161">Guid</span></span>|  
|<span data-ttu-id="3a4cd-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3a4cd-163">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-163">Int64</span></span>|  
|<span data-ttu-id="3a4cd-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3a4cd-165">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-165">Int64</span></span>|  
|<span data-ttu-id="3a4cd-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3a4cd-167">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-167">Int32</span></span>|  
|<span data-ttu-id="3a4cd-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="3a4cd-169">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-169">Int16</span></span>|  
|<span data-ttu-id="3a4cd-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="3a4cd-171">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-171">Int64</span></span>|  
|<span data-ttu-id="3a4cd-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3a4cd-173">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-173">String</span></span>|  
|<span data-ttu-id="3a4cd-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3a4cd-175">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-175">String</span></span>|  
|<span data-ttu-id="3a4cd-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3a4cd-177">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-177">String</span></span>|  
|<span data-ttu-id="3a4cd-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="3a4cd-179">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-179">String</span></span>|  
|<span data-ttu-id="3a4cd-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3a4cd-181">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-181">String</span></span>|  
|<span data-ttu-id="3a4cd-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-182">COLLATION_NAME</span></span>|<span data-ttu-id="3a4cd-183">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-183">String</span></span>|  
|<span data-ttu-id="3a4cd-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3a4cd-185">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-185">String</span></span>|  
|<span data-ttu-id="3a4cd-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3a4cd-187">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-187">String</span></span>|  
|<span data-ttu-id="3a4cd-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-188">DOMAIN_NAME</span></span>|<span data-ttu-id="3a4cd-189">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-189">String</span></span>|  
|<span data-ttu-id="3a4cd-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-190">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-191">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-191">String</span></span>|  
|<span data-ttu-id="3a4cd-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-192">COLUMN_LCID</span></span>|<span data-ttu-id="3a4cd-193">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-193">Int32</span></span>|  
|<span data-ttu-id="3a4cd-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="3a4cd-195">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-195">Int32</span></span>|  
|<span data-ttu-id="3a4cd-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-196">COLUMN_SORTID</span></span>|<span data-ttu-id="3a4cd-197">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-197">Int32</span></span>|  
|<span data-ttu-id="3a4cd-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="3a4cd-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-199">Byte[]</span></span>|  
|<span data-ttu-id="3a4cd-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-200">IS_COMPUTED</span></span>|<span data-ttu-id="3a4cd-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3a4cd-202">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-202">Procedures</span></span>  
  
|<span data-ttu-id="3a4cd-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-203">ColumnName</span></span>|<span data-ttu-id="3a4cd-204">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3a4cd-206">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-206">String</span></span>|  
|<span data-ttu-id="3a4cd-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-208">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-208">String</span></span>|  
|<span data-ttu-id="3a4cd-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="3a4cd-210">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-210">String</span></span>|  
|<span data-ttu-id="3a4cd-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3a4cd-212">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-212">Int16</span></span>|  
|<span data-ttu-id="3a4cd-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3a4cd-214">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-214">String</span></span>|  
|<span data-ttu-id="3a4cd-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-215">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-216">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-216">String</span></span>|  
|<span data-ttu-id="3a4cd-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-217">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-218">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-219">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="3a4cd-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3a4cd-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="3a4cd-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-222">ColumnName</span></span>|<span data-ttu-id="3a4cd-223">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3a4cd-225">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-225">String</span></span>|  
|<span data-ttu-id="3a4cd-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-227">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-227">String</span></span>|  
|<span data-ttu-id="3a4cd-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="3a4cd-229">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-229">String</span></span>|  
|<span data-ttu-id="3a4cd-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-230">PARAMETER_NAME</span></span>|<span data-ttu-id="3a4cd-231">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-231">String</span></span>|  
|<span data-ttu-id="3a4cd-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-233">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-233">Int32</span></span>|  
|<span data-ttu-id="3a4cd-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="3a4cd-235">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-235">Int32</span></span>|  
|<span data-ttu-id="3a4cd-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="3a4cd-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-237">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="3a4cd-239">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-239">String</span></span>|  
|<span data-ttu-id="3a4cd-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-240">IS_NULLABLE</span></span>|<span data-ttu-id="3a4cd-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-241">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-242">DATA_TYPE</span></span>|<span data-ttu-id="3a4cd-243">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-243">Int32</span></span>|  
|<span data-ttu-id="3a4cd-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3a4cd-245">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-245">Int64</span></span>|  
|<span data-ttu-id="3a4cd-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3a4cd-247">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-247">Int64</span></span>|  
|<span data-ttu-id="3a4cd-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3a4cd-249">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-249">Int32</span></span>|  
|<span data-ttu-id="3a4cd-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="3a4cd-251">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-251">Int16</span></span>|  
|<span data-ttu-id="3a4cd-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-252">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-253">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-253">String</span></span>|  
|<span data-ttu-id="3a4cd-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-254">TYPE_NAME</span></span>|<span data-ttu-id="3a4cd-255">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-255">String</span></span>|  
|<span data-ttu-id="3a4cd-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="3a4cd-257">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="3a4cd-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="3a4cd-258">Catalog</span></span>  
  
|<span data-ttu-id="3a4cd-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-259">ColumnName</span></span>|<span data-ttu-id="3a4cd-260">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-261">CATALOG_NAME</span></span>|<span data-ttu-id="3a4cd-262">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-262">String</span></span>|  
|<span data-ttu-id="3a4cd-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-263">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-264">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3a4cd-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-265">Indexes</span></span>  
  
|<span data-ttu-id="3a4cd-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-266">ColumnName</span></span>|<span data-ttu-id="3a4cd-267">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-268">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-269">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-269">String</span></span>|  
|<span data-ttu-id="3a4cd-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-271">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-271">String</span></span>|  
|<span data-ttu-id="3a4cd-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-272">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-273">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-273">String</span></span>|  
|<span data-ttu-id="3a4cd-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-274">INDEX_CATALOG</span></span>|<span data-ttu-id="3a4cd-275">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-275">String</span></span>|  
|<span data-ttu-id="3a4cd-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="3a4cd-277">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-277">String</span></span>|  
|<span data-ttu-id="3a4cd-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-278">INDEX_NAME</span></span>|<span data-ttu-id="3a4cd-279">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-279">String</span></span>|  
|<span data-ttu-id="3a4cd-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-280">PRIMARY_KEY</span></span>|<span data-ttu-id="3a4cd-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-281">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-282">UNIQUE</span></span>|<span data-ttu-id="3a4cd-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-283">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-284">CLUSTERED</span></span>|<span data-ttu-id="3a4cd-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-285">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-286">TYPE</span></span>|<span data-ttu-id="3a4cd-287">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-287">Int32</span></span>|  
|<span data-ttu-id="3a4cd-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3a4cd-288">FILL_FACTOR</span></span>|<span data-ttu-id="3a4cd-289">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-289">Int32</span></span>|  
|<span data-ttu-id="3a4cd-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-290">INITIAL_SIZE</span></span>|<span data-ttu-id="3a4cd-291">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-291">Int32</span></span>|  
|<span data-ttu-id="3a4cd-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-292">NULLS</span></span>|<span data-ttu-id="3a4cd-293">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-293">Int32</span></span>|  
|<span data-ttu-id="3a4cd-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3a4cd-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-295">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-296">AUTO_UPDATE</span></span>|<span data-ttu-id="3a4cd-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-297">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-298">NULL_COLLATION</span></span>|<span data-ttu-id="3a4cd-299">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-299">Int32</span></span>|  
|<span data-ttu-id="3a4cd-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-301">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-301">Int64</span></span>|  
|<span data-ttu-id="3a4cd-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-302">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-303">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-303">String</span></span>|  
|<span data-ttu-id="3a4cd-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-304">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-305">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-305">Guid</span></span>|  
|<span data-ttu-id="3a4cd-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-306">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-307">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-307">Int64</span></span>|  
|<span data-ttu-id="3a4cd-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-308">COLLATION</span></span>|<span data-ttu-id="3a4cd-309">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-309">Int16</span></span>|  
|<span data-ttu-id="3a4cd-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-310">CARDINALITY</span></span>|<span data-ttu-id="3a4cd-311">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="3a4cd-311">Decimal</span></span>|  
|<span data-ttu-id="3a4cd-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="3a4cd-312">PAGES</span></span>|<span data-ttu-id="3a4cd-313">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-313">Int32</span></span>|  
|<span data-ttu-id="3a4cd-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-314">FILTER_CONDITION</span></span>|<span data-ttu-id="3a4cd-315">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-315">String</span></span>|  
|<span data-ttu-id="3a4cd-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-316">INTEGRATED</span></span>|<span data-ttu-id="3a4cd-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="3a4cd-318">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="3a4cd-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="3a4cd-319">Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3a4cd-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3a4cd-320">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-320">Tables</span></span>  
  
-   <span data-ttu-id="3a4cd-321">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-321">Columns</span></span>  
  
-   <span data-ttu-id="3a4cd-322">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-322">Procedures</span></span>  
  
-   <span data-ttu-id="3a4cd-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3a4cd-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="3a4cd-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="3a4cd-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="3a4cd-325">ビュー</span><span class="sxs-lookup"><span data-stu-id="3a4cd-325">Views</span></span>  
  
-   <span data-ttu-id="3a4cd-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3a4cd-327">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-327">Tables</span></span>  
  
|<span data-ttu-id="3a4cd-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-328">ColumnName</span></span>|<span data-ttu-id="3a4cd-329">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-330">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-331">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-331">String</span></span>|  
|<span data-ttu-id="3a4cd-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-333">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-333">String</span></span>|  
|<span data-ttu-id="3a4cd-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-334">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-335">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-335">String</span></span>|  
|<span data-ttu-id="3a4cd-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-336">TABLE_TYPE</span></span>|<span data-ttu-id="3a4cd-337">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-337">String</span></span>|  
|<span data-ttu-id="3a4cd-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-338">TABLE_GUID</span></span>|<span data-ttu-id="3a4cd-339">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-339">Guid</span></span>|  
|<span data-ttu-id="3a4cd-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-340">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-341">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-341">String</span></span>|  
|<span data-ttu-id="3a4cd-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-342">TABLE_PROPID</span></span>|<span data-ttu-id="3a4cd-343">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-343">Int64</span></span>|  
|<span data-ttu-id="3a4cd-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-344">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-345">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-346">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3a4cd-348">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-348">Columns</span></span>  
  
|<span data-ttu-id="3a4cd-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-349">ColumnName</span></span>|<span data-ttu-id="3a4cd-350">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-351">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-352">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-352">String</span></span>|  
|<span data-ttu-id="3a4cd-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-354">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-354">String</span></span>|  
|<span data-ttu-id="3a4cd-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-355">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-356">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-356">String</span></span>|  
|<span data-ttu-id="3a4cd-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-357">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-358">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-358">String</span></span>|  
|<span data-ttu-id="3a4cd-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-359">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-360">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-360">Guid</span></span>|  
|<span data-ttu-id="3a4cd-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-361">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-362">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-362">Int64</span></span>|  
|<span data-ttu-id="3a4cd-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-364">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-364">Int64</span></span>|  
|<span data-ttu-id="3a4cd-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3a4cd-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-366">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3a4cd-368">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-368">String</span></span>|  
|<span data-ttu-id="3a4cd-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="3a4cd-370">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-370">Int64</span></span>|  
|<span data-ttu-id="3a4cd-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-371">IS_NULLABLE</span></span>|<span data-ttu-id="3a4cd-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-372">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-373">DATA_TYPE</span></span>|<span data-ttu-id="3a4cd-374">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-374">Int32</span></span>|  
|<span data-ttu-id="3a4cd-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-375">TYPE_GUID</span></span>|<span data-ttu-id="3a4cd-376">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-376">Guid</span></span>|  
|<span data-ttu-id="3a4cd-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3a4cd-378">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-378">Int64</span></span>|  
|<span data-ttu-id="3a4cd-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3a4cd-380">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-380">Int64</span></span>|  
|<span data-ttu-id="3a4cd-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3a4cd-382">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-382">Int32</span></span>|  
|<span data-ttu-id="3a4cd-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="3a4cd-384">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-384">Int16</span></span>|  
|<span data-ttu-id="3a4cd-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="3a4cd-386">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-386">Int64</span></span>|  
|<span data-ttu-id="3a4cd-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3a4cd-388">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-388">String</span></span>|  
|<span data-ttu-id="3a4cd-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3a4cd-390">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-390">String</span></span>|  
|<span data-ttu-id="3a4cd-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3a4cd-392">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-392">String</span></span>|  
|<span data-ttu-id="3a4cd-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="3a4cd-394">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-394">String</span></span>|  
|<span data-ttu-id="3a4cd-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3a4cd-396">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-396">String</span></span>|  
|<span data-ttu-id="3a4cd-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-397">COLLATION_NAME</span></span>|<span data-ttu-id="3a4cd-398">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-398">String</span></span>|  
|<span data-ttu-id="3a4cd-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3a4cd-400">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-400">String</span></span>|  
|<span data-ttu-id="3a4cd-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3a4cd-402">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-402">String</span></span>|  
|<span data-ttu-id="3a4cd-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-403">DOMAIN_NAME</span></span>|<span data-ttu-id="3a4cd-404">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-404">String</span></span>|  
|<span data-ttu-id="3a4cd-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-405">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-406">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3a4cd-407">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-407">Procedures</span></span>  
  
|<span data-ttu-id="3a4cd-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-408">ColumnName</span></span>|<span data-ttu-id="3a4cd-409">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3a4cd-411">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-411">String</span></span>|  
|<span data-ttu-id="3a4cd-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-413">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-413">String</span></span>|  
|<span data-ttu-id="3a4cd-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="3a4cd-415">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-415">String</span></span>|  
|<span data-ttu-id="3a4cd-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3a4cd-417">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-417">Int16</span></span>|  
|<span data-ttu-id="3a4cd-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3a4cd-419">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-419">String</span></span>|  
|<span data-ttu-id="3a4cd-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-420">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-421">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-421">String</span></span>|  
|<span data-ttu-id="3a4cd-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-422">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-423">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-424">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="3a4cd-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="3a4cd-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="3a4cd-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-427">ColumnName</span></span>|<span data-ttu-id="3a4cd-428">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3a4cd-430">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-430">String</span></span>|  
|<span data-ttu-id="3a4cd-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-432">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-432">String</span></span>|  
|<span data-ttu-id="3a4cd-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="3a4cd-434">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-434">String</span></span>|  
|<span data-ttu-id="3a4cd-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-435">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-436">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-436">String</span></span>|  
|<span data-ttu-id="3a4cd-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-437">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-438">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-438">Guid</span></span>|  
|<span data-ttu-id="3a4cd-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-439">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-440">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-440">Int64</span></span>|  
|<span data-ttu-id="3a4cd-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="3a4cd-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="3a4cd-442">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-442">Int64</span></span>|  
|<span data-ttu-id="3a4cd-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-444">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-444">Int64</span></span>|  
|<span data-ttu-id="3a4cd-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-445">IS_NULLABLE</span></span>|<span data-ttu-id="3a4cd-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-446">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-447">DATA_TYPE</span></span>|<span data-ttu-id="3a4cd-448">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-448">Int32</span></span>|  
|<span data-ttu-id="3a4cd-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-449">TYPE_GUID</span></span>|<span data-ttu-id="3a4cd-450">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-450">Guid</span></span>|  
|<span data-ttu-id="3a4cd-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3a4cd-452">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-452">Int64</span></span>|  
|<span data-ttu-id="3a4cd-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3a4cd-454">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-454">Int64</span></span>|  
|<span data-ttu-id="3a4cd-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3a4cd-456">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-456">Int32</span></span>|  
|<span data-ttu-id="3a4cd-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="3a4cd-458">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-458">Int16</span></span>|  
|<span data-ttu-id="3a4cd-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-459">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-460">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-460">String</span></span>|  
|<span data-ttu-id="3a4cd-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="3a4cd-461">OVERLOAD</span></span>|<span data-ttu-id="3a4cd-462">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3a4cd-463">ビュー</span><span class="sxs-lookup"><span data-stu-id="3a4cd-463">Views</span></span>  
  
|<span data-ttu-id="3a4cd-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-464">ColumnName</span></span>|<span data-ttu-id="3a4cd-465">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-466">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-467">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-467">String</span></span>|  
|<span data-ttu-id="3a4cd-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-469">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-469">String</span></span>|  
|<span data-ttu-id="3a4cd-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-470">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-471">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-471">String</span></span>|  
|<span data-ttu-id="3a4cd-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="3a4cd-473">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-473">String</span></span>|  
|<span data-ttu-id="3a4cd-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-474">CHECK_OPTION</span></span>|<span data-ttu-id="3a4cd-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-475">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-476">IS_UPDATABLE</span></span>|<span data-ttu-id="3a4cd-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-477">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-478">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-479">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-479">String</span></span>|  
|<span data-ttu-id="3a4cd-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-480">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-481">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-482">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3a4cd-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-484">Indexes</span></span>  
  
|<span data-ttu-id="3a4cd-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-485">ColumnName</span></span>|<span data-ttu-id="3a4cd-486">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-487">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-488">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-488">String</span></span>|  
|<span data-ttu-id="3a4cd-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-490">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-490">String</span></span>|  
|<span data-ttu-id="3a4cd-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-491">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-492">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-492">String</span></span>|  
|<span data-ttu-id="3a4cd-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-493">INDEX_CATALOG</span></span>|<span data-ttu-id="3a4cd-494">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-494">String</span></span>|  
|<span data-ttu-id="3a4cd-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="3a4cd-496">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-496">String</span></span>|  
|<span data-ttu-id="3a4cd-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-497">INDEX_NAME</span></span>|<span data-ttu-id="3a4cd-498">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-498">String</span></span>|  
|<span data-ttu-id="3a4cd-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-499">PRIMARY_KEY</span></span>|<span data-ttu-id="3a4cd-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-500">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-501">UNIQUE</span></span>|<span data-ttu-id="3a4cd-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-502">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-503">CLUSTERED</span></span>|<span data-ttu-id="3a4cd-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-504">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-505">TYPE</span></span>|<span data-ttu-id="3a4cd-506">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-506">Int32</span></span>|  
|<span data-ttu-id="3a4cd-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3a4cd-507">FILL_FACTOR</span></span>|<span data-ttu-id="3a4cd-508">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-508">Int32</span></span>|  
|<span data-ttu-id="3a4cd-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-509">INITIAL_SIZE</span></span>|<span data-ttu-id="3a4cd-510">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-510">Int32</span></span>|  
|<span data-ttu-id="3a4cd-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-511">NULLS</span></span>|<span data-ttu-id="3a4cd-512">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-512">Int32</span></span>|  
|<span data-ttu-id="3a4cd-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3a4cd-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-514">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-515">AUTO_UPDATE</span></span>|<span data-ttu-id="3a4cd-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-516">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-517">NULL_COLLATION</span></span>|<span data-ttu-id="3a4cd-518">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-518">Int32</span></span>|  
|<span data-ttu-id="3a4cd-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-520">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-520">Int64</span></span>|  
|<span data-ttu-id="3a4cd-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-521">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-522">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-522">String</span></span>|  
|<span data-ttu-id="3a4cd-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-523">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-524">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-524">Guid</span></span>|  
|<span data-ttu-id="3a4cd-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-525">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-526">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-526">Int64</span></span>|  
|<span data-ttu-id="3a4cd-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-527">COLLATION</span></span>|<span data-ttu-id="3a4cd-528">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-528">Int16</span></span>|  
|<span data-ttu-id="3a4cd-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-529">CARDINALITY</span></span>|<span data-ttu-id="3a4cd-530">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="3a4cd-530">Decimal</span></span>|  
|<span data-ttu-id="3a4cd-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="3a4cd-531">PAGES</span></span>|<span data-ttu-id="3a4cd-532">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-532">Int32</span></span>|  
|<span data-ttu-id="3a4cd-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-533">FILTER_CONDITION</span></span>|<span data-ttu-id="3a4cd-534">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-534">String</span></span>|  
|<span data-ttu-id="3a4cd-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-535">INTEGRATED</span></span>|<span data-ttu-id="3a4cd-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="3a4cd-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="3a4cd-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="3a4cd-538">Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="3a4cd-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="3a4cd-539">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-539">Tables</span></span>  
  
-   <span data-ttu-id="3a4cd-540">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-540">Columns</span></span>  
  
-   <span data-ttu-id="3a4cd-541">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-541">Procedures</span></span>  
  
-   <span data-ttu-id="3a4cd-542">ビュー</span><span class="sxs-lookup"><span data-stu-id="3a4cd-542">Views</span></span>  
  
-   <span data-ttu-id="3a4cd-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="3a4cd-544">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="3a4cd-544">Tables</span></span>  
  
|<span data-ttu-id="3a4cd-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-545">ColumnName</span></span>|<span data-ttu-id="3a4cd-546">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-547">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-548">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-548">String</span></span>|  
|<span data-ttu-id="3a4cd-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-550">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-550">String</span></span>|  
|<span data-ttu-id="3a4cd-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-551">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-552">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-552">String</span></span>|  
|<span data-ttu-id="3a4cd-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-553">TABLE_TYPE</span></span>|<span data-ttu-id="3a4cd-554">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-554">String</span></span>|  
|<span data-ttu-id="3a4cd-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-555">TABLE_GUID</span></span>|<span data-ttu-id="3a4cd-556">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-556">Guid</span></span>|  
|<span data-ttu-id="3a4cd-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-557">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-558">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-558">String</span></span>|  
|<span data-ttu-id="3a4cd-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-559">TABLE_PROPID</span></span>|<span data-ttu-id="3a4cd-560">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-560">Int64</span></span>|  
|<span data-ttu-id="3a4cd-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-561">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-562">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-563">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="3a4cd-565">列</span><span class="sxs-lookup"><span data-stu-id="3a4cd-565">Columns</span></span>  
  
|<span data-ttu-id="3a4cd-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-566">ColumnName</span></span>|<span data-ttu-id="3a4cd-567">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-568">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-569">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-569">String</span></span>|  
|<span data-ttu-id="3a4cd-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-571">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-571">String</span></span>|  
|<span data-ttu-id="3a4cd-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-572">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-573">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-573">String</span></span>|  
|<span data-ttu-id="3a4cd-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-574">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-575">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-575">String</span></span>|  
|<span data-ttu-id="3a4cd-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-576">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-577">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-577">Guid</span></span>|  
|<span data-ttu-id="3a4cd-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-578">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-579">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-579">Int64</span></span>|  
|<span data-ttu-id="3a4cd-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-581">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-581">Int64</span></span>|  
|<span data-ttu-id="3a4cd-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="3a4cd-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-583">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="3a4cd-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="3a4cd-585">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-585">String</span></span>|  
|<span data-ttu-id="3a4cd-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="3a4cd-587">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-587">Int64</span></span>|  
|<span data-ttu-id="3a4cd-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-588">IS_NULLABLE</span></span>|<span data-ttu-id="3a4cd-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-589">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-590">DATA_TYPE</span></span>|<span data-ttu-id="3a4cd-591">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-591">Int32</span></span>|  
|<span data-ttu-id="3a4cd-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-592">TYPE_GUID</span></span>|<span data-ttu-id="3a4cd-593">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-593">Guid</span></span>|  
|<span data-ttu-id="3a4cd-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="3a4cd-595">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-595">Int64</span></span>|  
|<span data-ttu-id="3a4cd-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="3a4cd-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="3a4cd-597">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-597">Int64</span></span>|  
|<span data-ttu-id="3a4cd-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="3a4cd-599">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-599">Int32</span></span>|  
|<span data-ttu-id="3a4cd-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="3a4cd-601">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-601">Int16</span></span>|  
|<span data-ttu-id="3a4cd-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="3a4cd-603">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-603">Int64</span></span>|  
|<span data-ttu-id="3a4cd-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="3a4cd-605">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-605">String</span></span>|  
|<span data-ttu-id="3a4cd-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="3a4cd-607">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-607">String</span></span>|  
|<span data-ttu-id="3a4cd-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="3a4cd-609">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-609">String</span></span>|  
|<span data-ttu-id="3a4cd-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="3a4cd-611">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-611">String</span></span>|  
|<span data-ttu-id="3a4cd-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="3a4cd-613">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-613">String</span></span>|  
|<span data-ttu-id="3a4cd-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-614">COLLATION_NAME</span></span>|<span data-ttu-id="3a4cd-615">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-615">String</span></span>|  
|<span data-ttu-id="3a4cd-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="3a4cd-617">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-617">String</span></span>|  
|<span data-ttu-id="3a4cd-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="3a4cd-619">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-619">String</span></span>|  
|<span data-ttu-id="3a4cd-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-620">DOMAIN_NAME</span></span>|<span data-ttu-id="3a4cd-621">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-621">String</span></span>|  
|<span data-ttu-id="3a4cd-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-622">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-623">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="3a4cd-624">手順</span><span class="sxs-lookup"><span data-stu-id="3a4cd-624">Procedures</span></span>  
  
|<span data-ttu-id="3a4cd-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-625">ColumnName</span></span>|<span data-ttu-id="3a4cd-626">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="3a4cd-628">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-628">String</span></span>|  
|<span data-ttu-id="3a4cd-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-630">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-630">String</span></span>|  
|<span data-ttu-id="3a4cd-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="3a4cd-632">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-632">String</span></span>|  
|<span data-ttu-id="3a4cd-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="3a4cd-634">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-634">Int16</span></span>|  
|<span data-ttu-id="3a4cd-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="3a4cd-636">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-636">String</span></span>|  
|<span data-ttu-id="3a4cd-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-637">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-638">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-638">String</span></span>|  
|<span data-ttu-id="3a4cd-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-639">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-640">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-641">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="3a4cd-643">ビュー</span><span class="sxs-lookup"><span data-stu-id="3a4cd-643">Views</span></span>  
  
|<span data-ttu-id="3a4cd-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-644">ColumnName</span></span>|<span data-ttu-id="3a4cd-645">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-646">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-647">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-647">String</span></span>|  
|<span data-ttu-id="3a4cd-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-649">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-649">String</span></span>|  
|<span data-ttu-id="3a4cd-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-650">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-651">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-651">String</span></span>|  
|<span data-ttu-id="3a4cd-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="3a4cd-653">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-653">String</span></span>|  
|<span data-ttu-id="3a4cd-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-654">CHECK_OPTION</span></span>|<span data-ttu-id="3a4cd-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-655">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-656">IS_UPDATABLE</span></span>|<span data-ttu-id="3a4cd-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-657">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-658">DESCRIPTION</span></span>|<span data-ttu-id="3a4cd-659">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-659">String</span></span>|  
|<span data-ttu-id="3a4cd-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-660">DATE_CREATED</span></span>|<span data-ttu-id="3a4cd-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-661">DateTime</span></span>|  
|<span data-ttu-id="3a4cd-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-662">DATE_MODIFIED</span></span>|<span data-ttu-id="3a4cd-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="3a4cd-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="3a4cd-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="3a4cd-664">Indexes</span></span>  
  
|<span data-ttu-id="3a4cd-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="3a4cd-665">ColumnName</span></span>|<span data-ttu-id="3a4cd-666">DataType</span><span class="sxs-lookup"><span data-stu-id="3a4cd-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="3a4cd-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-667">TABLE_CATALOG</span></span>|<span data-ttu-id="3a4cd-668">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-668">String</span></span>|  
|<span data-ttu-id="3a4cd-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="3a4cd-670">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-670">String</span></span>|  
|<span data-ttu-id="3a4cd-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-671">TABLE_NAME</span></span>|<span data-ttu-id="3a4cd-672">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-672">String</span></span>|  
|<span data-ttu-id="3a4cd-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="3a4cd-673">INDEX_CATALOG</span></span>|<span data-ttu-id="3a4cd-674">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-674">String</span></span>|  
|<span data-ttu-id="3a4cd-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="3a4cd-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="3a4cd-676">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-676">String</span></span>|  
|<span data-ttu-id="3a4cd-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-677">INDEX_NAME</span></span>|<span data-ttu-id="3a4cd-678">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-678">String</span></span>|  
|<span data-ttu-id="3a4cd-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-679">PRIMARY_KEY</span></span>|<span data-ttu-id="3a4cd-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-680">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-681">UNIQUE</span></span>|<span data-ttu-id="3a4cd-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-682">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-683">CLUSTERED</span></span>|<span data-ttu-id="3a4cd-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-684">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-685">TYPE</span></span>|<span data-ttu-id="3a4cd-686">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-686">Int32</span></span>|  
|<span data-ttu-id="3a4cd-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="3a4cd-687">FILL_FACTOR</span></span>|<span data-ttu-id="3a4cd-688">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-688">Int32</span></span>|  
|<span data-ttu-id="3a4cd-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-689">INITIAL_SIZE</span></span>|<span data-ttu-id="3a4cd-690">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-690">Int32</span></span>|  
|<span data-ttu-id="3a4cd-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-691">NULLS</span></span>|<span data-ttu-id="3a4cd-692">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-692">Int32</span></span>|  
|<span data-ttu-id="3a4cd-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="3a4cd-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="3a4cd-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-694">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="3a4cd-695">AUTO_UPDATE</span></span>|<span data-ttu-id="3a4cd-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="3a4cd-696">Boolean</span></span>|  
|<span data-ttu-id="3a4cd-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-697">NULL_COLLATION</span></span>|<span data-ttu-id="3a4cd-698">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-698">Int32</span></span>|  
|<span data-ttu-id="3a4cd-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="3a4cd-700">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-700">Int64</span></span>|  
|<span data-ttu-id="3a4cd-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="3a4cd-701">COLUMN_NAME</span></span>|<span data-ttu-id="3a4cd-702">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-702">String</span></span>|  
|<span data-ttu-id="3a4cd-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-703">COLUMN_GUID</span></span>|<span data-ttu-id="3a4cd-704">Guid</span><span class="sxs-lookup"><span data-stu-id="3a4cd-704">Guid</span></span>|  
|<span data-ttu-id="3a4cd-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="3a4cd-705">COLUMN_PROPID</span></span>|<span data-ttu-id="3a4cd-706">Int64</span><span class="sxs-lookup"><span data-stu-id="3a4cd-706">Int64</span></span>|  
|<span data-ttu-id="3a4cd-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-707">COLLATION</span></span>|<span data-ttu-id="3a4cd-708">Int16</span><span class="sxs-lookup"><span data-stu-id="3a4cd-708">Int16</span></span>|  
|<span data-ttu-id="3a4cd-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="3a4cd-709">CARDINALITY</span></span>|<span data-ttu-id="3a4cd-710">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="3a4cd-710">Decimal</span></span>|  
|<span data-ttu-id="3a4cd-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="3a4cd-711">PAGES</span></span>|<span data-ttu-id="3a4cd-712">Int32</span><span class="sxs-lookup"><span data-stu-id="3a4cd-712">Int32</span></span>|  
|<span data-ttu-id="3a4cd-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="3a4cd-713">FILTER_CONDITION</span></span>|<span data-ttu-id="3a4cd-714">String</span><span class="sxs-lookup"><span data-stu-id="3a4cd-714">String</span></span>|  
|<span data-ttu-id="3a4cd-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="3a4cd-715">INTEGRATED</span></span>|<span data-ttu-id="3a4cd-716">ブール型</span><span class="sxs-lookup"><span data-stu-id="3a4cd-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3a4cd-717">参照</span><span class="sxs-lookup"><span data-stu-id="3a4cd-717">See Also</span></span>  
 [<span data-ttu-id="3a4cd-718">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="3a4cd-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
