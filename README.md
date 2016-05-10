[![Build Status](https://travis-ci.org/grero/DirectionalRegression.jl.svg?branch=master)](https://travis-ci.org/grero/DirectionalRegression.jl) [![codecov](https://codecov.io/gh/grero/DirectionalRegression.jl/branch/master/graph/badge.svg)](https://codecov.io/gh/grero/DirectionalRegression.jl)

We can fit a Von Mises model like this
	
	using Distributions, DirectionalRegression
	X = 2*rand(1000,3)-1
	β = [0.181689,0.533594,0.132475]
	μ0 = g(X*β)
	θ = zeros(size(X,1))
	for i in 1:length(θ)
		 θ[i] = rand(sampler(VonMises(μ + μ0[i], κ)))
	end
	rr = fitmodel(X, θ, 2*pi*rand()-pi, 0.1+3*rand(); tol=1e-3, maxiter=100)



