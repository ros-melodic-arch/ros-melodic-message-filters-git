# Script generated with import_catkin_packages.py.
# For more information: https://github.com/bchretien/arch-ros-stacks.
pkgdesc="ROS - A set of message filters which take in messages and may output those messages at a later time, based on the conditions that filter needs met."
url='https://wiki.ros.org/message_filters'

pkgname='ros-melodic-message-filters-git'
pkgver='29053c4'
arch=('any')
pkgrel=1
license=('BSD')

ros_makedepends=(
	ros-melodic-rostest
	ros-melodic-rosunit
	ros-melodic-catkin
	ros-melodic-rosconsole
	ros-melodic-roscpp
)

makedepends=(
	'cmake'
	'ros-build-tools'
	${ros_makedepends[@]}
	boost
	'git'
)

ros_depends=(
	ros-melodic-rosconsole
	ros-melodic-roscpp
)

depends=(
	${ros_depends[@]}
)

provides=(
        'ros-melodic-message-filters'
)

conflicts=(
        'ros-melodic-message-filters'
)

_dir="ros_comm/utilities/message_filters"
source=("git+https://github.com/ros/ros_comm.git")
sha256sums=('SKIP')

build() {
	# Use ROS environment variables.
	source /usr/share/ros-build-tools/clear-ros-env.sh
	[ -f /opt/ros/melodic/setup.bash ] && source /opt/ros/melodic/setup.bash

	# Create the build directory.
	[ -d ${srcdir}/build ] || mkdir ${srcdir}/build
	cd ${srcdir}/build

	# Fix Python2/Python3 conflicts.
	/usr/share/ros-build-tools/fix-python-scripts.sh -v 3 ${srcdir}/${_dir}
	#Workaround for boost signals
        sed -i 's/signals//g' ${srcdir}/${_dir}/CMakeLists.txt

	# Build the project.
	cmake ${srcdir}/${_dir} \
		-DCMAKE_BUILD_TYPE=Release \
		-DCATKIN_BUILD_BINARY_PACKAGE=ON \
		-DCMAKE_INSTALL_PREFIX=/opt/ros/melodic \
		-DPYTHON_EXECUTABLE=/usr/bin/python3 \
		-DPYTHON_INCLUDE_DIR=/usr/include/python3.7m \
		-DPYTHON_LIBRARY=/usr/lib/libpython3.7m.so \
		-DPYTHON_BASENAME=.cpython-37m \
		-DSETUPTOOLS_DEB_LAYOUT=OFF
	make
}

package() {
	cd "${srcdir}/build"
	make DESTDIR="${pkgdir}/" install
}
