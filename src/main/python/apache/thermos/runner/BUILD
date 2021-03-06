#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
import os


python_library(
  name = '_runner',
  sources = rglobs('*.py'),
  dependencies = [
    '3rdparty/python:twitter.common.app',
    '3rdparty/python:twitter.common.log',
    'src/main/python/apache/thermos/common',
    'src/main/python/apache/thermos/config',
    'src/main/python/apache/thermos/core',
  ],
)

python_library(
  name = 'runner',
  dependencies = [
    ':_runner',
  ],
  provides = setup_py(
    name = 'apache.thermos.runner',
    version = open(os.path.join(get_buildroot(), '.auroraversion')).read().strip().upper(),
  ).with_binaries(
    thermos_runner = ':thermos_runner',
  ),
)

python_binary(
  name = 'thermos_runner',
  entry_point = 'apache.thermos.runner.thermos_runner',
  dependencies = [
    ':_runner',
  ],
)
