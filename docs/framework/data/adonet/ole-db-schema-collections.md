---
title: OLE DB スキーマ コレクション
ms.date: 03/30/2017
ms.assetid: 6380c36b-658e-4d67-91e8-7131ef4a7c2c
ms.openlocfilehash: f1cb5e1fe967088b44fa4045dfe50c1c57d963eb
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ole-db-schema-collections"></a><span data-ttu-id="01470-102">OLE DB スキーマ コレクション</span><span class="sxs-lookup"><span data-stu-id="01470-102">OLE DB Schema Collections</span></span>
<span data-ttu-id="01470-103">ここでは、Microsoft SQL Server、Oracle、および Microsoft Jet 用の各 OLE DB プロバイダーでのスキーマ コレクションのサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="01470-103">This section discusses schema collection support for the OLE DB providers for Microsoft SQL Server, Oracle, and Microsoft Jet.</span></span>  
  
## <a name="microsoft-sql-server-ole-db-provider"></a><span data-ttu-id="01470-104">Microsoft SQL Server OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="01470-104">Microsoft SQL Server OLE DB Provider</span></span>  
 <span data-ttu-id="01470-105">Microsoft SQL Server OLE DB Driver は、共通のスキーマ コレクションに加えて次の特定のスキーマ コレクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="01470-105">The Microsoft SQL Server OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="01470-106">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-106">Tables</span></span>  
  
-   <span data-ttu-id="01470-107">列</span><span class="sxs-lookup"><span data-stu-id="01470-107">Columns</span></span>  
  
-   <span data-ttu-id="01470-108">手順</span><span class="sxs-lookup"><span data-stu-id="01470-108">Procedures</span></span>  
  
-   <span data-ttu-id="01470-109">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="01470-109">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="01470-110">Catalog</span><span class="sxs-lookup"><span data-stu-id="01470-110">Catalog</span></span>  
  
-   <span data-ttu-id="01470-111">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-111">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="01470-112">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-112">Tables</span></span>  
  
|<span data-ttu-id="01470-113">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-113">ColumnName</span></span>|<span data-ttu-id="01470-114">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-114">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-115">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-115">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-116">String</span><span class="sxs-lookup"><span data-stu-id="01470-116">String</span></span>|  
|<span data-ttu-id="01470-117">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-117">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-118">String</span><span class="sxs-lookup"><span data-stu-id="01470-118">String</span></span>|  
|<span data-ttu-id="01470-119">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-119">TABLE_NAME</span></span>|<span data-ttu-id="01470-120">String</span><span class="sxs-lookup"><span data-stu-id="01470-120">String</span></span>|  
|<span data-ttu-id="01470-121">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-121">TABLE_TYPE</span></span>|<span data-ttu-id="01470-122">String</span><span class="sxs-lookup"><span data-stu-id="01470-122">String</span></span>|  
|<span data-ttu-id="01470-123">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-123">TABLE_GUID</span></span>|<span data-ttu-id="01470-124">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-124">Guid</span></span>|  
|<span data-ttu-id="01470-125">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-125">DESCRIPTION</span></span>|<span data-ttu-id="01470-126">String</span><span class="sxs-lookup"><span data-stu-id="01470-126">String</span></span>|  
|<span data-ttu-id="01470-127">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-127">TABLE_PROPID</span></span>|<span data-ttu-id="01470-128">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-128">Int64</span></span>|  
|<span data-ttu-id="01470-129">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-129">DATE_CREATED</span></span>|<span data-ttu-id="01470-130">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-130">DateTime</span></span>|  
|<span data-ttu-id="01470-131">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-131">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-132">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-132">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="01470-133">列</span><span class="sxs-lookup"><span data-stu-id="01470-133">Columns</span></span>  
  
|<span data-ttu-id="01470-134">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-134">ColumnName</span></span>|<span data-ttu-id="01470-135">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-135">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-136">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-136">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-137">String</span><span class="sxs-lookup"><span data-stu-id="01470-137">String</span></span>|  
|<span data-ttu-id="01470-138">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-138">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-139">String</span><span class="sxs-lookup"><span data-stu-id="01470-139">String</span></span>|  
|<span data-ttu-id="01470-140">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-140">TABLE_NAME</span></span>|<span data-ttu-id="01470-141">String</span><span class="sxs-lookup"><span data-stu-id="01470-141">String</span></span>|  
|<span data-ttu-id="01470-142">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-142">COLUMN_NAME</span></span>|<span data-ttu-id="01470-143">String</span><span class="sxs-lookup"><span data-stu-id="01470-143">String</span></span>|  
|<span data-ttu-id="01470-144">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-144">COLUMN_GUID</span></span>|<span data-ttu-id="01470-145">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-145">Guid</span></span>|  
|<span data-ttu-id="01470-146">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-146">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-147">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-147">Int64</span></span>|  
|<span data-ttu-id="01470-148">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-148">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-149">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-149">Int64</span></span>|  
|<span data-ttu-id="01470-150">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-150">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="01470-151">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-151">Boolean</span></span>|  
|<span data-ttu-id="01470-152">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-152">COLUMN_DEFAULT</span></span>|<span data-ttu-id="01470-153">String</span><span class="sxs-lookup"><span data-stu-id="01470-153">String</span></span>|  
|<span data-ttu-id="01470-154">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="01470-154">COLUMN_FLAGS</span></span>|<span data-ttu-id="01470-155">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-155">Int64</span></span>|  
|<span data-ttu-id="01470-156">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="01470-156">IS_NULLABLE</span></span>|<span data-ttu-id="01470-157">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-157">Boolean</span></span>|  
|<span data-ttu-id="01470-158">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-158">DATA_TYPE</span></span>|<span data-ttu-id="01470-159">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-159">Int32</span></span>|  
|<span data-ttu-id="01470-160">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-160">TYPE_GUID</span></span>|<span data-ttu-id="01470-161">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-161">Guid</span></span>|  
|<span data-ttu-id="01470-162">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-162">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="01470-163">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-163">Int64</span></span>|  
|<span data-ttu-id="01470-164">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-164">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="01470-165">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-165">Int64</span></span>|  
|<span data-ttu-id="01470-166">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-166">NUMERIC_PRECISION</span></span>|<span data-ttu-id="01470-167">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-167">Int32</span></span>|  
|<span data-ttu-id="01470-168">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="01470-168">NUMERIC_SCALE</span></span>|<span data-ttu-id="01470-169">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-169">Int16</span></span>|  
|<span data-ttu-id="01470-170">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-170">DATETIME_PRECISION</span></span>|<span data-ttu-id="01470-171">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-171">Int64</span></span>|  
|<span data-ttu-id="01470-172">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-172">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="01470-173">String</span><span class="sxs-lookup"><span data-stu-id="01470-173">String</span></span>|  
|<span data-ttu-id="01470-174">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-174">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="01470-175">String</span><span class="sxs-lookup"><span data-stu-id="01470-175">String</span></span>|  
|<span data-ttu-id="01470-176">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-176">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="01470-177">String</span><span class="sxs-lookup"><span data-stu-id="01470-177">String</span></span>|  
|<span data-ttu-id="01470-178">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-178">COLLATION_CATALOG</span></span>|<span data-ttu-id="01470-179">String</span><span class="sxs-lookup"><span data-stu-id="01470-179">String</span></span>|  
|<span data-ttu-id="01470-180">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-180">COLLATION_SCHEMA</span></span>|<span data-ttu-id="01470-181">String</span><span class="sxs-lookup"><span data-stu-id="01470-181">String</span></span>|  
|<span data-ttu-id="01470-182">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-182">COLLATION_NAME</span></span>|<span data-ttu-id="01470-183">String</span><span class="sxs-lookup"><span data-stu-id="01470-183">String</span></span>|  
|<span data-ttu-id="01470-184">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-184">DOMAIN_CATALOG</span></span>|<span data-ttu-id="01470-185">String</span><span class="sxs-lookup"><span data-stu-id="01470-185">String</span></span>|  
|<span data-ttu-id="01470-186">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-186">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="01470-187">String</span><span class="sxs-lookup"><span data-stu-id="01470-187">String</span></span>|  
|<span data-ttu-id="01470-188">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-188">DOMAIN_NAME</span></span>|<span data-ttu-id="01470-189">String</span><span class="sxs-lookup"><span data-stu-id="01470-189">String</span></span>|  
|<span data-ttu-id="01470-190">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-190">DESCRIPTION</span></span>|<span data-ttu-id="01470-191">String</span><span class="sxs-lookup"><span data-stu-id="01470-191">String</span></span>|  
|<span data-ttu-id="01470-192">COLUMN_LCID</span><span class="sxs-lookup"><span data-stu-id="01470-192">COLUMN_LCID</span></span>|<span data-ttu-id="01470-193">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-193">Int32</span></span>|  
|<span data-ttu-id="01470-194">COLUMN_COMPFLAGS</span><span class="sxs-lookup"><span data-stu-id="01470-194">COLUMN_COMPFLAGS</span></span>|<span data-ttu-id="01470-195">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-195">Int32</span></span>|  
|<span data-ttu-id="01470-196">COLUMN_SORTID</span><span class="sxs-lookup"><span data-stu-id="01470-196">COLUMN_SORTID</span></span>|<span data-ttu-id="01470-197">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-197">Int32</span></span>|  
|<span data-ttu-id="01470-198">COLUMN_TDSCOLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-198">COLUMN_TDSCOLLATION</span></span>|<span data-ttu-id="01470-199">Byte[]</span><span class="sxs-lookup"><span data-stu-id="01470-199">Byte[]</span></span>|  
|<span data-ttu-id="01470-200">IS_COMPUTED</span><span class="sxs-lookup"><span data-stu-id="01470-200">IS_COMPUTED</span></span>|<span data-ttu-id="01470-201">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-201">Boolean</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="01470-202">手順</span><span class="sxs-lookup"><span data-stu-id="01470-202">Procedures</span></span>  
  
|<span data-ttu-id="01470-203">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-203">ColumnName</span></span>|<span data-ttu-id="01470-204">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-204">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-205">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-205">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="01470-206">String</span><span class="sxs-lookup"><span data-stu-id="01470-206">String</span></span>|  
|<span data-ttu-id="01470-207">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-207">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="01470-208">String</span><span class="sxs-lookup"><span data-stu-id="01470-208">String</span></span>|  
|<span data-ttu-id="01470-209">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-209">PROCEDURE_NAME</span></span>|<span data-ttu-id="01470-210">String</span><span class="sxs-lookup"><span data-stu-id="01470-210">String</span></span>|  
|<span data-ttu-id="01470-211">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-211">PROCEDURE_TYPE</span></span>|<span data-ttu-id="01470-212">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-212">Int16</span></span>|  
|<span data-ttu-id="01470-213">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="01470-213">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="01470-214">String</span><span class="sxs-lookup"><span data-stu-id="01470-214">String</span></span>|  
|<span data-ttu-id="01470-215">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-215">DESCRIPTION</span></span>|<span data-ttu-id="01470-216">String</span><span class="sxs-lookup"><span data-stu-id="01470-216">String</span></span>|  
|<span data-ttu-id="01470-217">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-217">DATE_CREATED</span></span>|<span data-ttu-id="01470-218">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-218">DateTime</span></span>|  
|<span data-ttu-id="01470-219">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-219">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-220">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-220">DateTime</span></span>|  
  
### <a name="procedureparameters"></a><span data-ttu-id="01470-221">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="01470-221">ProcedureParameters</span></span>  
  
|<span data-ttu-id="01470-222">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-222">ColumnName</span></span>|<span data-ttu-id="01470-223">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-223">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-224">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-224">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="01470-225">String</span><span class="sxs-lookup"><span data-stu-id="01470-225">String</span></span>|  
|<span data-ttu-id="01470-226">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-226">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="01470-227">String</span><span class="sxs-lookup"><span data-stu-id="01470-227">String</span></span>|  
|<span data-ttu-id="01470-228">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-228">PROCEDURE_NAME</span></span>|<span data-ttu-id="01470-229">String</span><span class="sxs-lookup"><span data-stu-id="01470-229">String</span></span>|  
|<span data-ttu-id="01470-230">PARAMETER_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-230">PARAMETER_NAME</span></span>|<span data-ttu-id="01470-231">String</span><span class="sxs-lookup"><span data-stu-id="01470-231">String</span></span>|  
|<span data-ttu-id="01470-232">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-232">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-233">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-233">Int32</span></span>|  
|<span data-ttu-id="01470-234">PARAMETER_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-234">PARAMETER_TYPE</span></span>|<span data-ttu-id="01470-235">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-235">Int32</span></span>|  
|<span data-ttu-id="01470-236">PARAMETER_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-236">PARAMETER_HASDEFAULT</span></span>|<span data-ttu-id="01470-237">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-237">Boolean</span></span>|  
|<span data-ttu-id="01470-238">PARAMETER_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-238">PARAMETER_DEFAULT</span></span>|<span data-ttu-id="01470-239">String</span><span class="sxs-lookup"><span data-stu-id="01470-239">String</span></span>|  
|<span data-ttu-id="01470-240">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="01470-240">IS_NULLABLE</span></span>|<span data-ttu-id="01470-241">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-241">Boolean</span></span>|  
|<span data-ttu-id="01470-242">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-242">DATA_TYPE</span></span>|<span data-ttu-id="01470-243">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-243">Int32</span></span>|  
|<span data-ttu-id="01470-244">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-244">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="01470-245">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-245">Int64</span></span>|  
|<span data-ttu-id="01470-246">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-246">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="01470-247">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-247">Int64</span></span>|  
|<span data-ttu-id="01470-248">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-248">NUMERIC_PRECISION</span></span>|<span data-ttu-id="01470-249">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-249">Int32</span></span>|  
|<span data-ttu-id="01470-250">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="01470-250">NUMERIC_SCALE</span></span>|<span data-ttu-id="01470-251">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-251">Int16</span></span>|  
|<span data-ttu-id="01470-252">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-252">DESCRIPTION</span></span>|<span data-ttu-id="01470-253">String</span><span class="sxs-lookup"><span data-stu-id="01470-253">String</span></span>|  
|<span data-ttu-id="01470-254">TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-254">TYPE_NAME</span></span>|<span data-ttu-id="01470-255">String</span><span class="sxs-lookup"><span data-stu-id="01470-255">String</span></span>|  
|<span data-ttu-id="01470-256">LOCAL_TYPE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-256">LOCAL_TYPE_NAME</span></span>|<span data-ttu-id="01470-257">String</span><span class="sxs-lookup"><span data-stu-id="01470-257">String</span></span>|  
  
### <a name="catalog"></a><span data-ttu-id="01470-258">Catalog</span><span class="sxs-lookup"><span data-stu-id="01470-258">Catalog</span></span>  
  
|<span data-ttu-id="01470-259">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-259">ColumnName</span></span>|<span data-ttu-id="01470-260">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-260">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-261">CATALOG_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-261">CATALOG_NAME</span></span>|<span data-ttu-id="01470-262">String</span><span class="sxs-lookup"><span data-stu-id="01470-262">String</span></span>|  
|<span data-ttu-id="01470-263">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-263">DESCRIPTION</span></span>|<span data-ttu-id="01470-264">String</span><span class="sxs-lookup"><span data-stu-id="01470-264">String</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="01470-265">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-265">Indexes</span></span>  
  
|<span data-ttu-id="01470-266">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-266">ColumnName</span></span>|<span data-ttu-id="01470-267">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-267">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-268">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-268">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-269">String</span><span class="sxs-lookup"><span data-stu-id="01470-269">String</span></span>|  
|<span data-ttu-id="01470-270">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-270">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-271">String</span><span class="sxs-lookup"><span data-stu-id="01470-271">String</span></span>|  
|<span data-ttu-id="01470-272">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-272">TABLE_NAME</span></span>|<span data-ttu-id="01470-273">String</span><span class="sxs-lookup"><span data-stu-id="01470-273">String</span></span>|  
|<span data-ttu-id="01470-274">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-274">INDEX_CATALOG</span></span>|<span data-ttu-id="01470-275">String</span><span class="sxs-lookup"><span data-stu-id="01470-275">String</span></span>|  
|<span data-ttu-id="01470-276">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-276">INDEX_SCHEMA</span></span>|<span data-ttu-id="01470-277">String</span><span class="sxs-lookup"><span data-stu-id="01470-277">String</span></span>|  
|<span data-ttu-id="01470-278">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-278">INDEX_NAME</span></span>|<span data-ttu-id="01470-279">String</span><span class="sxs-lookup"><span data-stu-id="01470-279">String</span></span>|  
|<span data-ttu-id="01470-280">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="01470-280">PRIMARY_KEY</span></span>|<span data-ttu-id="01470-281">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-281">Boolean</span></span>|  
|<span data-ttu-id="01470-282">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="01470-282">UNIQUE</span></span>|<span data-ttu-id="01470-283">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-283">Boolean</span></span>|  
|<span data-ttu-id="01470-284">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="01470-284">CLUSTERED</span></span>|<span data-ttu-id="01470-285">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-285">Boolean</span></span>|  
|<span data-ttu-id="01470-286">TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-286">TYPE</span></span>|<span data-ttu-id="01470-287">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-287">Int32</span></span>|  
|<span data-ttu-id="01470-288">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="01470-288">FILL_FACTOR</span></span>|<span data-ttu-id="01470-289">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-289">Int32</span></span>|  
|<span data-ttu-id="01470-290">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="01470-290">INITIAL_SIZE</span></span>|<span data-ttu-id="01470-291">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-291">Int32</span></span>|  
|<span data-ttu-id="01470-292">NULLS</span><span class="sxs-lookup"><span data-stu-id="01470-292">NULLS</span></span>|<span data-ttu-id="01470-293">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-293">Int32</span></span>|  
|<span data-ttu-id="01470-294">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="01470-294">SORT_BOOKMARKS</span></span>|<span data-ttu-id="01470-295">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-295">Boolean</span></span>|  
|<span data-ttu-id="01470-296">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="01470-296">AUTO_UPDATE</span></span>|<span data-ttu-id="01470-297">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-297">Boolean</span></span>|  
|<span data-ttu-id="01470-298">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-298">NULL_COLLATION</span></span>|<span data-ttu-id="01470-299">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-299">Int32</span></span>|  
|<span data-ttu-id="01470-300">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-300">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-301">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-301">Int64</span></span>|  
|<span data-ttu-id="01470-302">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-302">COLUMN_NAME</span></span>|<span data-ttu-id="01470-303">String</span><span class="sxs-lookup"><span data-stu-id="01470-303">String</span></span>|  
|<span data-ttu-id="01470-304">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-304">COLUMN_GUID</span></span>|<span data-ttu-id="01470-305">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-305">Guid</span></span>|  
|<span data-ttu-id="01470-306">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-306">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-307">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-307">Int64</span></span>|  
|<span data-ttu-id="01470-308">COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-308">COLLATION</span></span>|<span data-ttu-id="01470-309">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-309">Int16</span></span>|  
|<span data-ttu-id="01470-310">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="01470-310">CARDINALITY</span></span>|<span data-ttu-id="01470-311">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="01470-311">Decimal</span></span>|  
|<span data-ttu-id="01470-312">PAGES</span><span class="sxs-lookup"><span data-stu-id="01470-312">PAGES</span></span>|<span data-ttu-id="01470-313">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-313">Int32</span></span>|  
|<span data-ttu-id="01470-314">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="01470-314">FILTER_CONDITION</span></span>|<span data-ttu-id="01470-315">String</span><span class="sxs-lookup"><span data-stu-id="01470-315">String</span></span>|  
|<span data-ttu-id="01470-316">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="01470-316">INTEGRATED</span></span>|<span data-ttu-id="01470-317">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-317">Boolean</span></span>|  
  
## <a name="microsoft-oracle-ole-db-provider"></a><span data-ttu-id="01470-318">Microsoft Oracle OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="01470-318">Microsoft Oracle OLE DB Provider</span></span>  
 <span data-ttu-id="01470-319">Microsoft Oracle OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="01470-319">The Microsoft Oracle OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="01470-320">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-320">Tables</span></span>  
  
-   <span data-ttu-id="01470-321">列</span><span class="sxs-lookup"><span data-stu-id="01470-321">Columns</span></span>  
  
-   <span data-ttu-id="01470-322">手順</span><span class="sxs-lookup"><span data-stu-id="01470-322">Procedures</span></span>  
  
-   <span data-ttu-id="01470-323">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="01470-323">ProcedureColumns</span></span>  
  
-   <span data-ttu-id="01470-324">ProcedureParameters</span><span class="sxs-lookup"><span data-stu-id="01470-324">ProcedureParameters</span></span>  
  
-   <span data-ttu-id="01470-325">ビュー</span><span class="sxs-lookup"><span data-stu-id="01470-325">Views</span></span>  
  
-   <span data-ttu-id="01470-326">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-326">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="01470-327">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-327">Tables</span></span>  
  
|<span data-ttu-id="01470-328">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-328">ColumnName</span></span>|<span data-ttu-id="01470-329">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-329">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-330">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-330">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-331">String</span><span class="sxs-lookup"><span data-stu-id="01470-331">String</span></span>|  
|<span data-ttu-id="01470-332">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-332">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-333">String</span><span class="sxs-lookup"><span data-stu-id="01470-333">String</span></span>|  
|<span data-ttu-id="01470-334">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-334">TABLE_NAME</span></span>|<span data-ttu-id="01470-335">String</span><span class="sxs-lookup"><span data-stu-id="01470-335">String</span></span>|  
|<span data-ttu-id="01470-336">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-336">TABLE_TYPE</span></span>|<span data-ttu-id="01470-337">String</span><span class="sxs-lookup"><span data-stu-id="01470-337">String</span></span>|  
|<span data-ttu-id="01470-338">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-338">TABLE_GUID</span></span>|<span data-ttu-id="01470-339">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-339">Guid</span></span>|  
|<span data-ttu-id="01470-340">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-340">DESCRIPTION</span></span>|<span data-ttu-id="01470-341">String</span><span class="sxs-lookup"><span data-stu-id="01470-341">String</span></span>|  
|<span data-ttu-id="01470-342">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-342">TABLE_PROPID</span></span>|<span data-ttu-id="01470-343">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-343">Int64</span></span>|  
|<span data-ttu-id="01470-344">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-344">DATE_CREATED</span></span>|<span data-ttu-id="01470-345">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-345">DateTime</span></span>|  
|<span data-ttu-id="01470-346">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-346">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-347">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-347">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="01470-348">列</span><span class="sxs-lookup"><span data-stu-id="01470-348">Columns</span></span>  
  
|<span data-ttu-id="01470-349">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-349">ColumnName</span></span>|<span data-ttu-id="01470-350">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-350">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-351">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-351">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-352">String</span><span class="sxs-lookup"><span data-stu-id="01470-352">String</span></span>|  
|<span data-ttu-id="01470-353">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-353">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-354">String</span><span class="sxs-lookup"><span data-stu-id="01470-354">String</span></span>|  
|<span data-ttu-id="01470-355">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-355">TABLE_NAME</span></span>|<span data-ttu-id="01470-356">String</span><span class="sxs-lookup"><span data-stu-id="01470-356">String</span></span>|  
|<span data-ttu-id="01470-357">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-357">COLUMN_NAME</span></span>|<span data-ttu-id="01470-358">String</span><span class="sxs-lookup"><span data-stu-id="01470-358">String</span></span>|  
|<span data-ttu-id="01470-359">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-359">COLUMN_GUID</span></span>|<span data-ttu-id="01470-360">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-360">Guid</span></span>|  
|<span data-ttu-id="01470-361">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-361">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-362">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-362">Int64</span></span>|  
|<span data-ttu-id="01470-363">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-363">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-364">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-364">Int64</span></span>|  
|<span data-ttu-id="01470-365">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-365">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="01470-366">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-366">Boolean</span></span>|  
|<span data-ttu-id="01470-367">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-367">COLUMN_DEFAULT</span></span>|<span data-ttu-id="01470-368">String</span><span class="sxs-lookup"><span data-stu-id="01470-368">String</span></span>|  
|<span data-ttu-id="01470-369">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="01470-369">COLUMN_FLAGS</span></span>|<span data-ttu-id="01470-370">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-370">Int64</span></span>|  
|<span data-ttu-id="01470-371">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="01470-371">IS_NULLABLE</span></span>|<span data-ttu-id="01470-372">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-372">Boolean</span></span>|  
|<span data-ttu-id="01470-373">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-373">DATA_TYPE</span></span>|<span data-ttu-id="01470-374">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-374">Int32</span></span>|  
|<span data-ttu-id="01470-375">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-375">TYPE_GUID</span></span>|<span data-ttu-id="01470-376">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-376">Guid</span></span>|  
|<span data-ttu-id="01470-377">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-377">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="01470-378">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-378">Int64</span></span>|  
|<span data-ttu-id="01470-379">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-379">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="01470-380">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-380">Int64</span></span>|  
|<span data-ttu-id="01470-381">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-381">NUMERIC_PRECISION</span></span>|<span data-ttu-id="01470-382">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-382">Int32</span></span>|  
|<span data-ttu-id="01470-383">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="01470-383">NUMERIC_SCALE</span></span>|<span data-ttu-id="01470-384">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-384">Int16</span></span>|  
|<span data-ttu-id="01470-385">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-385">DATETIME_PRECISION</span></span>|<span data-ttu-id="01470-386">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-386">Int64</span></span>|  
|<span data-ttu-id="01470-387">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-387">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="01470-388">String</span><span class="sxs-lookup"><span data-stu-id="01470-388">String</span></span>|  
|<span data-ttu-id="01470-389">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-389">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="01470-390">String</span><span class="sxs-lookup"><span data-stu-id="01470-390">String</span></span>|  
|<span data-ttu-id="01470-391">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-391">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="01470-392">String</span><span class="sxs-lookup"><span data-stu-id="01470-392">String</span></span>|  
|<span data-ttu-id="01470-393">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-393">COLLATION_CATALOG</span></span>|<span data-ttu-id="01470-394">String</span><span class="sxs-lookup"><span data-stu-id="01470-394">String</span></span>|  
|<span data-ttu-id="01470-395">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-395">COLLATION_SCHEMA</span></span>|<span data-ttu-id="01470-396">String</span><span class="sxs-lookup"><span data-stu-id="01470-396">String</span></span>|  
|<span data-ttu-id="01470-397">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-397">COLLATION_NAME</span></span>|<span data-ttu-id="01470-398">String</span><span class="sxs-lookup"><span data-stu-id="01470-398">String</span></span>|  
|<span data-ttu-id="01470-399">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-399">DOMAIN_CATALOG</span></span>|<span data-ttu-id="01470-400">String</span><span class="sxs-lookup"><span data-stu-id="01470-400">String</span></span>|  
|<span data-ttu-id="01470-401">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-401">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="01470-402">String</span><span class="sxs-lookup"><span data-stu-id="01470-402">String</span></span>|  
|<span data-ttu-id="01470-403">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-403">DOMAIN_NAME</span></span>|<span data-ttu-id="01470-404">String</span><span class="sxs-lookup"><span data-stu-id="01470-404">String</span></span>|  
|<span data-ttu-id="01470-405">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-405">DESCRIPTION</span></span>|<span data-ttu-id="01470-406">String</span><span class="sxs-lookup"><span data-stu-id="01470-406">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="01470-407">手順</span><span class="sxs-lookup"><span data-stu-id="01470-407">Procedures</span></span>  
  
|<span data-ttu-id="01470-408">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-408">ColumnName</span></span>|<span data-ttu-id="01470-409">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-409">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-410">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-410">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="01470-411">String</span><span class="sxs-lookup"><span data-stu-id="01470-411">String</span></span>|  
|<span data-ttu-id="01470-412">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-412">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="01470-413">String</span><span class="sxs-lookup"><span data-stu-id="01470-413">String</span></span>|  
|<span data-ttu-id="01470-414">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-414">PROCEDURE_NAME</span></span>|<span data-ttu-id="01470-415">String</span><span class="sxs-lookup"><span data-stu-id="01470-415">String</span></span>|  
|<span data-ttu-id="01470-416">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-416">PROCEDURE_TYPE</span></span>|<span data-ttu-id="01470-417">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-417">Int16</span></span>|  
|<span data-ttu-id="01470-418">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="01470-418">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="01470-419">String</span><span class="sxs-lookup"><span data-stu-id="01470-419">String</span></span>|  
|<span data-ttu-id="01470-420">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-420">DESCRIPTION</span></span>|<span data-ttu-id="01470-421">String</span><span class="sxs-lookup"><span data-stu-id="01470-421">String</span></span>|  
|<span data-ttu-id="01470-422">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-422">DATE_CREATED</span></span>|<span data-ttu-id="01470-423">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-423">DateTime</span></span>|  
|<span data-ttu-id="01470-424">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-424">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-425">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-425">DateTime</span></span>|  
  
### <a name="procedurecolumns"></a><span data-ttu-id="01470-426">ProcedureColumns</span><span class="sxs-lookup"><span data-stu-id="01470-426">ProcedureColumns</span></span>  
  
|<span data-ttu-id="01470-427">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-427">ColumnName</span></span>|<span data-ttu-id="01470-428">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-428">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-429">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-429">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="01470-430">String</span><span class="sxs-lookup"><span data-stu-id="01470-430">String</span></span>|  
|<span data-ttu-id="01470-431">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-431">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="01470-432">String</span><span class="sxs-lookup"><span data-stu-id="01470-432">String</span></span>|  
|<span data-ttu-id="01470-433">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-433">PROCEDURE_NAME</span></span>|<span data-ttu-id="01470-434">String</span><span class="sxs-lookup"><span data-stu-id="01470-434">String</span></span>|  
|<span data-ttu-id="01470-435">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-435">COLUMN_NAME</span></span>|<span data-ttu-id="01470-436">String</span><span class="sxs-lookup"><span data-stu-id="01470-436">String</span></span>|  
|<span data-ttu-id="01470-437">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-437">COLUMN_GUID</span></span>|<span data-ttu-id="01470-438">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-438">Guid</span></span>|  
|<span data-ttu-id="01470-439">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-439">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-440">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-440">Int64</span></span>|  
|<span data-ttu-id="01470-441">ROWSET_NUMBER</span><span class="sxs-lookup"><span data-stu-id="01470-441">ROWSET_NUMBER</span></span>|<span data-ttu-id="01470-442">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-442">Int64</span></span>|  
|<span data-ttu-id="01470-443">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-443">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-444">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-444">Int64</span></span>|  
|<span data-ttu-id="01470-445">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="01470-445">IS_NULLABLE</span></span>|<span data-ttu-id="01470-446">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-446">Boolean</span></span>|  
|<span data-ttu-id="01470-447">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-447">DATA_TYPE</span></span>|<span data-ttu-id="01470-448">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-448">Int32</span></span>|  
|<span data-ttu-id="01470-449">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-449">TYPE_GUID</span></span>|<span data-ttu-id="01470-450">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-450">Guid</span></span>|  
|<span data-ttu-id="01470-451">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-451">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="01470-452">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-452">Int64</span></span>|  
|<span data-ttu-id="01470-453">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-453">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="01470-454">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-454">Int64</span></span>|  
|<span data-ttu-id="01470-455">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-455">NUMERIC_PRECISION</span></span>|<span data-ttu-id="01470-456">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-456">Int32</span></span>|  
|<span data-ttu-id="01470-457">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="01470-457">NUMERIC_SCALE</span></span>|<span data-ttu-id="01470-458">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-458">Int16</span></span>|  
|<span data-ttu-id="01470-459">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-459">DESCRIPTION</span></span>|<span data-ttu-id="01470-460">String</span><span class="sxs-lookup"><span data-stu-id="01470-460">String</span></span>|  
|<span data-ttu-id="01470-461">OVERLOAD</span><span class="sxs-lookup"><span data-stu-id="01470-461">OVERLOAD</span></span>|<span data-ttu-id="01470-462">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-462">Int16</span></span>|  
  
### <a name="views"></a><span data-ttu-id="01470-463">ビュー</span><span class="sxs-lookup"><span data-stu-id="01470-463">Views</span></span>  
  
|<span data-ttu-id="01470-464">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-464">ColumnName</span></span>|<span data-ttu-id="01470-465">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-465">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-466">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-466">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-467">String</span><span class="sxs-lookup"><span data-stu-id="01470-467">String</span></span>|  
|<span data-ttu-id="01470-468">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-468">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-469">String</span><span class="sxs-lookup"><span data-stu-id="01470-469">String</span></span>|  
|<span data-ttu-id="01470-470">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-470">TABLE_NAME</span></span>|<span data-ttu-id="01470-471">String</span><span class="sxs-lookup"><span data-stu-id="01470-471">String</span></span>|  
|<span data-ttu-id="01470-472">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="01470-472">VIEW_DEFINITION</span></span>|<span data-ttu-id="01470-473">String</span><span class="sxs-lookup"><span data-stu-id="01470-473">String</span></span>|  
|<span data-ttu-id="01470-474">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="01470-474">CHECK_OPTION</span></span>|<span data-ttu-id="01470-475">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-475">Boolean</span></span>|  
|<span data-ttu-id="01470-476">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="01470-476">IS_UPDATABLE</span></span>|<span data-ttu-id="01470-477">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-477">Boolean</span></span>|  
|<span data-ttu-id="01470-478">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-478">DESCRIPTION</span></span>|<span data-ttu-id="01470-479">String</span><span class="sxs-lookup"><span data-stu-id="01470-479">String</span></span>|  
|<span data-ttu-id="01470-480">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-480">DATE_CREATED</span></span>|<span data-ttu-id="01470-481">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-481">DateTime</span></span>|  
|<span data-ttu-id="01470-482">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-482">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-483">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-483">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="01470-484">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-484">Indexes</span></span>  
  
|<span data-ttu-id="01470-485">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-485">ColumnName</span></span>|<span data-ttu-id="01470-486">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-486">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-487">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-487">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-488">String</span><span class="sxs-lookup"><span data-stu-id="01470-488">String</span></span>|  
|<span data-ttu-id="01470-489">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-489">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-490">String</span><span class="sxs-lookup"><span data-stu-id="01470-490">String</span></span>|  
|<span data-ttu-id="01470-491">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-491">TABLE_NAME</span></span>|<span data-ttu-id="01470-492">String</span><span class="sxs-lookup"><span data-stu-id="01470-492">String</span></span>|  
|<span data-ttu-id="01470-493">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-493">INDEX_CATALOG</span></span>|<span data-ttu-id="01470-494">String</span><span class="sxs-lookup"><span data-stu-id="01470-494">String</span></span>|  
|<span data-ttu-id="01470-495">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-495">INDEX_SCHEMA</span></span>|<span data-ttu-id="01470-496">String</span><span class="sxs-lookup"><span data-stu-id="01470-496">String</span></span>|  
|<span data-ttu-id="01470-497">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-497">INDEX_NAME</span></span>|<span data-ttu-id="01470-498">String</span><span class="sxs-lookup"><span data-stu-id="01470-498">String</span></span>|  
|<span data-ttu-id="01470-499">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="01470-499">PRIMARY_KEY</span></span>|<span data-ttu-id="01470-500">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-500">Boolean</span></span>|  
|<span data-ttu-id="01470-501">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="01470-501">UNIQUE</span></span>|<span data-ttu-id="01470-502">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-502">Boolean</span></span>|  
|<span data-ttu-id="01470-503">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="01470-503">CLUSTERED</span></span>|<span data-ttu-id="01470-504">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-504">Boolean</span></span>|  
|<span data-ttu-id="01470-505">TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-505">TYPE</span></span>|<span data-ttu-id="01470-506">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-506">Int32</span></span>|  
|<span data-ttu-id="01470-507">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="01470-507">FILL_FACTOR</span></span>|<span data-ttu-id="01470-508">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-508">Int32</span></span>|  
|<span data-ttu-id="01470-509">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="01470-509">INITIAL_SIZE</span></span>|<span data-ttu-id="01470-510">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-510">Int32</span></span>|  
|<span data-ttu-id="01470-511">NULLS</span><span class="sxs-lookup"><span data-stu-id="01470-511">NULLS</span></span>|<span data-ttu-id="01470-512">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-512">Int32</span></span>|  
|<span data-ttu-id="01470-513">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="01470-513">SORT_BOOKMARKS</span></span>|<span data-ttu-id="01470-514">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-514">Boolean</span></span>|  
|<span data-ttu-id="01470-515">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="01470-515">AUTO_UPDATE</span></span>|<span data-ttu-id="01470-516">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-516">Boolean</span></span>|  
|<span data-ttu-id="01470-517">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-517">NULL_COLLATION</span></span>|<span data-ttu-id="01470-518">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-518">Int32</span></span>|  
|<span data-ttu-id="01470-519">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-519">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-520">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-520">Int64</span></span>|  
|<span data-ttu-id="01470-521">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-521">COLUMN_NAME</span></span>|<span data-ttu-id="01470-522">String</span><span class="sxs-lookup"><span data-stu-id="01470-522">String</span></span>|  
|<span data-ttu-id="01470-523">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-523">COLUMN_GUID</span></span>|<span data-ttu-id="01470-524">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-524">Guid</span></span>|  
|<span data-ttu-id="01470-525">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-525">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-526">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-526">Int64</span></span>|  
|<span data-ttu-id="01470-527">COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-527">COLLATION</span></span>|<span data-ttu-id="01470-528">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-528">Int16</span></span>|  
|<span data-ttu-id="01470-529">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="01470-529">CARDINALITY</span></span>|<span data-ttu-id="01470-530">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="01470-530">Decimal</span></span>|  
|<span data-ttu-id="01470-531">PAGES</span><span class="sxs-lookup"><span data-stu-id="01470-531">PAGES</span></span>|<span data-ttu-id="01470-532">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-532">Int32</span></span>|  
|<span data-ttu-id="01470-533">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="01470-533">FILTER_CONDITION</span></span>|<span data-ttu-id="01470-534">String</span><span class="sxs-lookup"><span data-stu-id="01470-534">String</span></span>|  
|<span data-ttu-id="01470-535">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="01470-535">INTEGRATED</span></span>|<span data-ttu-id="01470-536">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-536">Boolean</span></span>|  
  
## <a name="microsoft-jet-ole-db-provider"></a><span data-ttu-id="01470-537">Microsoft Jet OLE DB Provider</span><span class="sxs-lookup"><span data-stu-id="01470-537">Microsoft Jet OLE DB Provider</span></span>  
 <span data-ttu-id="01470-538">Microsoft Jet OLE DB Driver は、共通のスキーマ コレクションに加えて次のスキーマ コレクションをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="01470-538">The Microsoft Jet OLE DB Driver supports the following specific schema collections in addition to the common schema collections:</span></span>  
  
-   <span data-ttu-id="01470-539">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-539">Tables</span></span>  
  
-   <span data-ttu-id="01470-540">列</span><span class="sxs-lookup"><span data-stu-id="01470-540">Columns</span></span>  
  
-   <span data-ttu-id="01470-541">手順</span><span class="sxs-lookup"><span data-stu-id="01470-541">Procedures</span></span>  
  
-   <span data-ttu-id="01470-542">ビュー</span><span class="sxs-lookup"><span data-stu-id="01470-542">Views</span></span>  
  
-   <span data-ttu-id="01470-543">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-543">Indexes</span></span>  
  
### <a name="tables"></a><span data-ttu-id="01470-544">[テーブル]</span><span class="sxs-lookup"><span data-stu-id="01470-544">Tables</span></span>  
  
|<span data-ttu-id="01470-545">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-545">ColumnName</span></span>|<span data-ttu-id="01470-546">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-546">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-547">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-547">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-548">String</span><span class="sxs-lookup"><span data-stu-id="01470-548">String</span></span>|  
|<span data-ttu-id="01470-549">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-549">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-550">String</span><span class="sxs-lookup"><span data-stu-id="01470-550">String</span></span>|  
|<span data-ttu-id="01470-551">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-551">TABLE_NAME</span></span>|<span data-ttu-id="01470-552">String</span><span class="sxs-lookup"><span data-stu-id="01470-552">String</span></span>|  
|<span data-ttu-id="01470-553">TABLE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-553">TABLE_TYPE</span></span>|<span data-ttu-id="01470-554">String</span><span class="sxs-lookup"><span data-stu-id="01470-554">String</span></span>|  
|<span data-ttu-id="01470-555">TABLE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-555">TABLE_GUID</span></span>|<span data-ttu-id="01470-556">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-556">Guid</span></span>|  
|<span data-ttu-id="01470-557">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-557">DESCRIPTION</span></span>|<span data-ttu-id="01470-558">String</span><span class="sxs-lookup"><span data-stu-id="01470-558">String</span></span>|  
|<span data-ttu-id="01470-559">TABLE_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-559">TABLE_PROPID</span></span>|<span data-ttu-id="01470-560">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-560">Int64</span></span>|  
|<span data-ttu-id="01470-561">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-561">DATE_CREATED</span></span>|<span data-ttu-id="01470-562">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-562">DateTime</span></span>|  
|<span data-ttu-id="01470-563">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-563">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-564">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-564">DateTime</span></span>|  
  
### <a name="columns"></a><span data-ttu-id="01470-565">列</span><span class="sxs-lookup"><span data-stu-id="01470-565">Columns</span></span>  
  
|<span data-ttu-id="01470-566">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-566">ColumnName</span></span>|<span data-ttu-id="01470-567">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-567">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-568">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-568">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-569">String</span><span class="sxs-lookup"><span data-stu-id="01470-569">String</span></span>|  
|<span data-ttu-id="01470-570">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-570">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-571">String</span><span class="sxs-lookup"><span data-stu-id="01470-571">String</span></span>|  
|<span data-ttu-id="01470-572">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-572">TABLE_NAME</span></span>|<span data-ttu-id="01470-573">String</span><span class="sxs-lookup"><span data-stu-id="01470-573">String</span></span>|  
|<span data-ttu-id="01470-574">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-574">COLUMN_NAME</span></span>|<span data-ttu-id="01470-575">String</span><span class="sxs-lookup"><span data-stu-id="01470-575">String</span></span>|  
|<span data-ttu-id="01470-576">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-576">COLUMN_GUID</span></span>|<span data-ttu-id="01470-577">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-577">Guid</span></span>|  
|<span data-ttu-id="01470-578">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-578">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-579">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-579">Int64</span></span>|  
|<span data-ttu-id="01470-580">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-580">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-581">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-581">Int64</span></span>|  
|<span data-ttu-id="01470-582">COLUMN_HASDEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-582">COLUMN_HASDEFAULT</span></span>|<span data-ttu-id="01470-583">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-583">Boolean</span></span>|  
|<span data-ttu-id="01470-584">COLUMN_DEFAULT</span><span class="sxs-lookup"><span data-stu-id="01470-584">COLUMN_DEFAULT</span></span>|<span data-ttu-id="01470-585">String</span><span class="sxs-lookup"><span data-stu-id="01470-585">String</span></span>|  
|<span data-ttu-id="01470-586">COLUMN_FLAGS</span><span class="sxs-lookup"><span data-stu-id="01470-586">COLUMN_FLAGS</span></span>|<span data-ttu-id="01470-587">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-587">Int64</span></span>|  
|<span data-ttu-id="01470-588">IS_NULLABLE</span><span class="sxs-lookup"><span data-stu-id="01470-588">IS_NULLABLE</span></span>|<span data-ttu-id="01470-589">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-589">Boolean</span></span>|  
|<span data-ttu-id="01470-590">DATA_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-590">DATA_TYPE</span></span>|<span data-ttu-id="01470-591">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-591">Int32</span></span>|  
|<span data-ttu-id="01470-592">TYPE_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-592">TYPE_GUID</span></span>|<span data-ttu-id="01470-593">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-593">Guid</span></span>|  
|<span data-ttu-id="01470-594">CHARACTER_MAXIMUM_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-594">CHARACTER_MAXIMUM_LENGTH</span></span>|<span data-ttu-id="01470-595">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-595">Int64</span></span>|  
|<span data-ttu-id="01470-596">CHARACTER_OCTET_LENGTH</span><span class="sxs-lookup"><span data-stu-id="01470-596">CHARACTER_OCTET_LENGTH</span></span>|<span data-ttu-id="01470-597">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-597">Int64</span></span>|  
|<span data-ttu-id="01470-598">NUMERIC_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-598">NUMERIC_PRECISION</span></span>|<span data-ttu-id="01470-599">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-599">Int32</span></span>|  
|<span data-ttu-id="01470-600">NUMERIC_SCALE</span><span class="sxs-lookup"><span data-stu-id="01470-600">NUMERIC_SCALE</span></span>|<span data-ttu-id="01470-601">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-601">Int16</span></span>|  
|<span data-ttu-id="01470-602">DATETIME_PRECISION</span><span class="sxs-lookup"><span data-stu-id="01470-602">DATETIME_PRECISION</span></span>|<span data-ttu-id="01470-603">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-603">Int64</span></span>|  
|<span data-ttu-id="01470-604">CHARACTER_SET_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-604">CHARACTER_SET_CATALOG</span></span>|<span data-ttu-id="01470-605">String</span><span class="sxs-lookup"><span data-stu-id="01470-605">String</span></span>|  
|<span data-ttu-id="01470-606">CHARACTER_SET_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-606">CHARACTER_SET_SCHEMA</span></span>|<span data-ttu-id="01470-607">String</span><span class="sxs-lookup"><span data-stu-id="01470-607">String</span></span>|  
|<span data-ttu-id="01470-608">CHARACTER_SET_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-608">CHARACTER_SET_NAME</span></span>|<span data-ttu-id="01470-609">String</span><span class="sxs-lookup"><span data-stu-id="01470-609">String</span></span>|  
|<span data-ttu-id="01470-610">COLLATION_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-610">COLLATION_CATALOG</span></span>|<span data-ttu-id="01470-611">String</span><span class="sxs-lookup"><span data-stu-id="01470-611">String</span></span>|  
|<span data-ttu-id="01470-612">COLLATION_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-612">COLLATION_SCHEMA</span></span>|<span data-ttu-id="01470-613">String</span><span class="sxs-lookup"><span data-stu-id="01470-613">String</span></span>|  
|<span data-ttu-id="01470-614">COLLATION_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-614">COLLATION_NAME</span></span>|<span data-ttu-id="01470-615">String</span><span class="sxs-lookup"><span data-stu-id="01470-615">String</span></span>|  
|<span data-ttu-id="01470-616">DOMAIN_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-616">DOMAIN_CATALOG</span></span>|<span data-ttu-id="01470-617">String</span><span class="sxs-lookup"><span data-stu-id="01470-617">String</span></span>|  
|<span data-ttu-id="01470-618">DOMAIN_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-618">DOMAIN_SCHEMA</span></span>|<span data-ttu-id="01470-619">String</span><span class="sxs-lookup"><span data-stu-id="01470-619">String</span></span>|  
|<span data-ttu-id="01470-620">DOMAIN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-620">DOMAIN_NAME</span></span>|<span data-ttu-id="01470-621">String</span><span class="sxs-lookup"><span data-stu-id="01470-621">String</span></span>|  
|<span data-ttu-id="01470-622">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-622">DESCRIPTION</span></span>|<span data-ttu-id="01470-623">String</span><span class="sxs-lookup"><span data-stu-id="01470-623">String</span></span>|  
  
### <a name="procedures"></a><span data-ttu-id="01470-624">手順</span><span class="sxs-lookup"><span data-stu-id="01470-624">Procedures</span></span>  
  
|<span data-ttu-id="01470-625">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-625">ColumnName</span></span>|<span data-ttu-id="01470-626">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-626">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-627">PROCEDURE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-627">PROCEDURE_CATALOG</span></span>|<span data-ttu-id="01470-628">String</span><span class="sxs-lookup"><span data-stu-id="01470-628">String</span></span>|  
|<span data-ttu-id="01470-629">PROCEDURE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-629">PROCEDURE_SCHEMA</span></span>|<span data-ttu-id="01470-630">String</span><span class="sxs-lookup"><span data-stu-id="01470-630">String</span></span>|  
|<span data-ttu-id="01470-631">PROCEDURE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-631">PROCEDURE_NAME</span></span>|<span data-ttu-id="01470-632">String</span><span class="sxs-lookup"><span data-stu-id="01470-632">String</span></span>|  
|<span data-ttu-id="01470-633">PROCEDURE_TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-633">PROCEDURE_TYPE</span></span>|<span data-ttu-id="01470-634">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-634">Int16</span></span>|  
|<span data-ttu-id="01470-635">PROCEDURE_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="01470-635">PROCEDURE_DEFINITION</span></span>|<span data-ttu-id="01470-636">String</span><span class="sxs-lookup"><span data-stu-id="01470-636">String</span></span>|  
|<span data-ttu-id="01470-637">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-637">DESCRIPTION</span></span>|<span data-ttu-id="01470-638">String</span><span class="sxs-lookup"><span data-stu-id="01470-638">String</span></span>|  
|<span data-ttu-id="01470-639">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-639">DATE_CREATED</span></span>|<span data-ttu-id="01470-640">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-640">DateTime</span></span>|  
|<span data-ttu-id="01470-641">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-641">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-642">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-642">DateTime</span></span>|  
  
### <a name="views"></a><span data-ttu-id="01470-643">ビュー</span><span class="sxs-lookup"><span data-stu-id="01470-643">Views</span></span>  
  
|<span data-ttu-id="01470-644">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-644">ColumnName</span></span>|<span data-ttu-id="01470-645">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-645">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-646">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-646">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-647">String</span><span class="sxs-lookup"><span data-stu-id="01470-647">String</span></span>|  
|<span data-ttu-id="01470-648">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-648">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-649">String</span><span class="sxs-lookup"><span data-stu-id="01470-649">String</span></span>|  
|<span data-ttu-id="01470-650">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-650">TABLE_NAME</span></span>|<span data-ttu-id="01470-651">String</span><span class="sxs-lookup"><span data-stu-id="01470-651">String</span></span>|  
|<span data-ttu-id="01470-652">VIEW_DEFINITION</span><span class="sxs-lookup"><span data-stu-id="01470-652">VIEW_DEFINITION</span></span>|<span data-ttu-id="01470-653">String</span><span class="sxs-lookup"><span data-stu-id="01470-653">String</span></span>|  
|<span data-ttu-id="01470-654">CHECK_OPTION</span><span class="sxs-lookup"><span data-stu-id="01470-654">CHECK_OPTION</span></span>|<span data-ttu-id="01470-655">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-655">Boolean</span></span>|  
|<span data-ttu-id="01470-656">IS_UPDATABLE</span><span class="sxs-lookup"><span data-stu-id="01470-656">IS_UPDATABLE</span></span>|<span data-ttu-id="01470-657">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-657">Boolean</span></span>|  
|<span data-ttu-id="01470-658">DESCRIPTION</span><span class="sxs-lookup"><span data-stu-id="01470-658">DESCRIPTION</span></span>|<span data-ttu-id="01470-659">String</span><span class="sxs-lookup"><span data-stu-id="01470-659">String</span></span>|  
|<span data-ttu-id="01470-660">DATE_CREATED</span><span class="sxs-lookup"><span data-stu-id="01470-660">DATE_CREATED</span></span>|<span data-ttu-id="01470-661">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-661">DateTime</span></span>|  
|<span data-ttu-id="01470-662">DATE_MODIFIED</span><span class="sxs-lookup"><span data-stu-id="01470-662">DATE_MODIFIED</span></span>|<span data-ttu-id="01470-663">DateTime</span><span class="sxs-lookup"><span data-stu-id="01470-663">DateTime</span></span>|  
  
### <a name="indexes"></a><span data-ttu-id="01470-664">Indexes</span><span class="sxs-lookup"><span data-stu-id="01470-664">Indexes</span></span>  
  
|<span data-ttu-id="01470-665">ColumnName</span><span class="sxs-lookup"><span data-stu-id="01470-665">ColumnName</span></span>|<span data-ttu-id="01470-666">DataType</span><span class="sxs-lookup"><span data-stu-id="01470-666">DataType</span></span>|  
|----------------|--------------|  
|<span data-ttu-id="01470-667">TABLE_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-667">TABLE_CATALOG</span></span>|<span data-ttu-id="01470-668">String</span><span class="sxs-lookup"><span data-stu-id="01470-668">String</span></span>|  
|<span data-ttu-id="01470-669">TABLE_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-669">TABLE_SCHEMA</span></span>|<span data-ttu-id="01470-670">String</span><span class="sxs-lookup"><span data-stu-id="01470-670">String</span></span>|  
|<span data-ttu-id="01470-671">TABLE_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-671">TABLE_NAME</span></span>|<span data-ttu-id="01470-672">String</span><span class="sxs-lookup"><span data-stu-id="01470-672">String</span></span>|  
|<span data-ttu-id="01470-673">INDEX_CATALOG</span><span class="sxs-lookup"><span data-stu-id="01470-673">INDEX_CATALOG</span></span>|<span data-ttu-id="01470-674">String</span><span class="sxs-lookup"><span data-stu-id="01470-674">String</span></span>|  
|<span data-ttu-id="01470-675">INDEX_SCHEMA</span><span class="sxs-lookup"><span data-stu-id="01470-675">INDEX_SCHEMA</span></span>|<span data-ttu-id="01470-676">String</span><span class="sxs-lookup"><span data-stu-id="01470-676">String</span></span>|  
|<span data-ttu-id="01470-677">INDEX_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-677">INDEX_NAME</span></span>|<span data-ttu-id="01470-678">String</span><span class="sxs-lookup"><span data-stu-id="01470-678">String</span></span>|  
|<span data-ttu-id="01470-679">PRIMARY_KEY</span><span class="sxs-lookup"><span data-stu-id="01470-679">PRIMARY_KEY</span></span>|<span data-ttu-id="01470-680">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-680">Boolean</span></span>|  
|<span data-ttu-id="01470-681">UNIQUE</span><span class="sxs-lookup"><span data-stu-id="01470-681">UNIQUE</span></span>|<span data-ttu-id="01470-682">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-682">Boolean</span></span>|  
|<span data-ttu-id="01470-683">CLUSTERED</span><span class="sxs-lookup"><span data-stu-id="01470-683">CLUSTERED</span></span>|<span data-ttu-id="01470-684">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-684">Boolean</span></span>|  
|<span data-ttu-id="01470-685">TYPE</span><span class="sxs-lookup"><span data-stu-id="01470-685">TYPE</span></span>|<span data-ttu-id="01470-686">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-686">Int32</span></span>|  
|<span data-ttu-id="01470-687">FILL_FACTOR</span><span class="sxs-lookup"><span data-stu-id="01470-687">FILL_FACTOR</span></span>|<span data-ttu-id="01470-688">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-688">Int32</span></span>|  
|<span data-ttu-id="01470-689">INITIAL_SIZE</span><span class="sxs-lookup"><span data-stu-id="01470-689">INITIAL_SIZE</span></span>|<span data-ttu-id="01470-690">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-690">Int32</span></span>|  
|<span data-ttu-id="01470-691">NULLS</span><span class="sxs-lookup"><span data-stu-id="01470-691">NULLS</span></span>|<span data-ttu-id="01470-692">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-692">Int32</span></span>|  
|<span data-ttu-id="01470-693">SORT_BOOKMARKS</span><span class="sxs-lookup"><span data-stu-id="01470-693">SORT_BOOKMARKS</span></span>|<span data-ttu-id="01470-694">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-694">Boolean</span></span>|  
|<span data-ttu-id="01470-695">AUTO_UPDATE</span><span class="sxs-lookup"><span data-stu-id="01470-695">AUTO_UPDATE</span></span>|<span data-ttu-id="01470-696">Boolean</span><span class="sxs-lookup"><span data-stu-id="01470-696">Boolean</span></span>|  
|<span data-ttu-id="01470-697">NULL_COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-697">NULL_COLLATION</span></span>|<span data-ttu-id="01470-698">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-698">Int32</span></span>|  
|<span data-ttu-id="01470-699">ORDINAL_POSITION</span><span class="sxs-lookup"><span data-stu-id="01470-699">ORDINAL_POSITION</span></span>|<span data-ttu-id="01470-700">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-700">Int64</span></span>|  
|<span data-ttu-id="01470-701">COLUMN_NAME</span><span class="sxs-lookup"><span data-stu-id="01470-701">COLUMN_NAME</span></span>|<span data-ttu-id="01470-702">String</span><span class="sxs-lookup"><span data-stu-id="01470-702">String</span></span>|  
|<span data-ttu-id="01470-703">COLUMN_GUID</span><span class="sxs-lookup"><span data-stu-id="01470-703">COLUMN_GUID</span></span>|<span data-ttu-id="01470-704">Guid</span><span class="sxs-lookup"><span data-stu-id="01470-704">Guid</span></span>|  
|<span data-ttu-id="01470-705">COLUMN_PROPID</span><span class="sxs-lookup"><span data-stu-id="01470-705">COLUMN_PROPID</span></span>|<span data-ttu-id="01470-706">Int64</span><span class="sxs-lookup"><span data-stu-id="01470-706">Int64</span></span>|  
|<span data-ttu-id="01470-707">COLLATION</span><span class="sxs-lookup"><span data-stu-id="01470-707">COLLATION</span></span>|<span data-ttu-id="01470-708">Int16</span><span class="sxs-lookup"><span data-stu-id="01470-708">Int16</span></span>|  
|<span data-ttu-id="01470-709">CARDINALITY</span><span class="sxs-lookup"><span data-stu-id="01470-709">CARDINALITY</span></span>|<span data-ttu-id="01470-710">Decimal (10 進数型)</span><span class="sxs-lookup"><span data-stu-id="01470-710">Decimal</span></span>|  
|<span data-ttu-id="01470-711">PAGES</span><span class="sxs-lookup"><span data-stu-id="01470-711">PAGES</span></span>|<span data-ttu-id="01470-712">Int32</span><span class="sxs-lookup"><span data-stu-id="01470-712">Int32</span></span>|  
|<span data-ttu-id="01470-713">FILTER_CONDITION</span><span class="sxs-lookup"><span data-stu-id="01470-713">FILTER_CONDITION</span></span>|<span data-ttu-id="01470-714">String</span><span class="sxs-lookup"><span data-stu-id="01470-714">String</span></span>|  
|<span data-ttu-id="01470-715">INTEGRATED</span><span class="sxs-lookup"><span data-stu-id="01470-715">INTEGRATED</span></span>|<span data-ttu-id="01470-716">ブール型</span><span class="sxs-lookup"><span data-stu-id="01470-716">Boolean</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01470-717">関連項目</span><span class="sxs-lookup"><span data-stu-id="01470-717">See Also</span></span>  
 [<span data-ttu-id="01470-718">ADO.NET のマネージ プロバイダーと DataSet デベロッパー センター</span><span class="sxs-lookup"><span data-stu-id="01470-718">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
