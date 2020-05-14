get_token:

kubectl -n user-compte-de-test describe secret $(kubectl -n user-compte-de-test get secret | grep compte-de-test | awk '{print $1}')

namespace : user-compte-de-test
