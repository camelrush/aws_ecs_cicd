# -----------------------
#  Create stack
# -----------------------
# 0.ecr
aws cloudformation create-stack --stack-name ecscicd-ecr \
    --template-body file://template/0.ecr.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 

# 1.network
aws cloudformation create-stack --stack-name ecscicd-network \
    --template-body file://template/1.network.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 

# 2.backend
aws cloudformation create-stack --stack-name ecscicd-backend \
    --template-body file://template/2.backend.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 3.frontend
aws cloudformation create-stack --stack-name ecscicd-frontend \
    --template-body file://template/3.frontend.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 4.cdn
aws cloudformation create-stack --stack-name ecscicd-cdn \
    --template-body file://template/4.cdn.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 \
    --parameters file://parameter/parameter_cdn.json

# 8.pipeline
aws cloudformation create-stack --stack-name ecscicd-pipeline \
    --template-body file://template/8.pipeline.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 9.oidc_from_github
aws cloudformation create-stack --stack-name ecscicd-oidc \
    --template-body file://template/9.oidc_from_github.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 \
    --parameters file://parameter/parameter_oidc.json

# -----------------------
#  Update stack
# -----------------------
# 0.ecr
aws cloudformation update-stack --stack-name ecscicd-ecr \
    --template-body file://template/0.ecr.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 

# 1.network
aws cloudformation update-stack --stack-name ecscicd-network \
    --template-body file://template/1.network.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 

# 2.backend
aws cloudformation update-stack --stack-name ecscicd-backend \
    --template-body file://template/2.backend.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 3.frontend
aws cloudformation update-stack --stack-name ecscicd-frontend \
    --template-body file://template/3.frontend.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 4.cdn
aws cloudformation update-stack --stack-name ecscicd-cdn \
    --template-body file://template/4.cdn.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 \
    --parameters file://parameter/parameter_cdn.json

# 8.pipeline
aws cloudformation update-stack --stack-name ecscicd-pipeline \
    --template-body file://template/8.pipeline.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1

# 9.oidc_from_github
aws cloudformation update-stack --stack-name ecscicd-oidc \
    --template-body file://template/9.oidc_from_github.yaml \
    --capabilities CAPABILITY_NAMED_IAM \
    --region ap-northeast-1 \
    --parameters file://parameter/parameter_oidc.json
