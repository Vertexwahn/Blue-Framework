#
#   This file is part of BlueFramework, a simple 3D engine.
#	Copyright (c) 2019 Technical University of Munich
#	Chair of Computational Modeling and Simulation.
#   
#   BlueFramework is free software; you can redistribute it and/or modify
#   it under the terms of the GNU General Public License Version 3
#   as published by the Free Software Foundation.
#   
#   BlueFramework is distributed in the hope that it will be useful,
#   but WITHOUT ANY WARRANTY; without even the implied warranty of
#   MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the
#   GNU General Public License for more details.
#   
#   You should have received a copy of the GNU General Public License
#   along with this program. If not, see <http://www.gnu.org/licenses/>.
#

file(GLOB BlueFramework_D3D11RenderSystem_Source                          src/BlueFramework/D3D11RenderSystem/*.*)

file(GLOB_RECURSE BlueFramework_D3D11RenderSystem_Headers				   src/BlueFramework/D3D11RenderSystem/*.h)

source_group(BlueFramework\\D3D11RenderSystem                             FILES ${BlueFramework_D3D11RenderSystem_Source})

add_library(BlueFramework.D3D11RenderSystem SHARED
    ${BlueFramework_D3D11RenderSystem_Source}
)

target_include_directories(BlueFramework.D3D11RenderSystem
	PUBLIC
		src
)

target_link_libraries(BlueFramework.D3D11RenderSystem
	PUBLIC
		BlueFramework.Core
		BlueFramework.Rasterizer
		BlueFramework.ImageProcessing
		tinyxml2
	PRIVATE
		#DirectX11 libs linked in source.
)

install(TARGETS BlueFramework.D3D11RenderSystem   
   ARCHIVE DESTINATION lib/${MSVC_VERSION_STRING}/${CMAKE_VS_PLATFORM_NAME}/$<CONFIG>
   COMPONENT library_files
)

install(DIRECTORY src/BlueFramework/D3D11RenderSystem/ DESTINATION include/BlueFramework/D3D11RenderSystem
		COMPONENT include
        FILES_MATCHING PATTERN "*.h"
)

install(DIRECTORY src/BlueFramework/D3D11RenderSystem/ DESTINATION src/BlueFramework/D3D11RenderSystem
		COMPONENT source
        FILES_MATCHING PATTERN "*.cpp" PATTERN "*.h"
)